## State diagrams

```mermaid
    stateDiagram-v2
        state if_state <<choice>>
        [*] --> IsPositive
        IsPositive --> if_state
        if_state --> False: if n < 0
        if_state --> True : if n >= 0
```
## Entity Relationship Diagrams

```mermaid
    erDiagram
        CUSTOMER ||--o{ ORDER : places
        CUSTOMER {
            string name
            string custNumber
            string sector
        }
        ORDER ||--|{ LINE-ITEM : contains
        ORDER {
            int orderNumber
            string deliveryAddress
        }
        LINE-ITEM {
            string productCode
            int quantity
            float pricePerUnit
        }
```
## Architecture Diagrams

```mermaid
    architecture-beta
        group api(cloud)[API]
    
        service db(database)[Database] in api
        service disk1(disk)[Storage] in api
        service disk2(disk)[Storage] in api
        service server(server)[Server] in api
    
        db:L -- R:server
        disk1:T -- B:server
        disk2:T -- B:db
```

## Sequence Diagram

```mermaid
    sequenceDiagram
        autonumber
        participant web as Web Browser
        participant blog as Blog Service
        participant account as Account Service
        participant mail as Mail Service
        participant db as Storage
    
        Note over web,db: The user must be logged in to submit blog posts
        web->>+account: Logs in using credentials
        account->>db: Query stored accounts
        db->>account: Respond with query result
    
        alt Credentials not found
            account->>web: Invalid credentials
        else Credentials found
            account->>-web: Successfully logged in
    
            Note over web,db: When the user is authenticated, they can now submit new posts
            web->>+blog: Submit new post
            blog->>db: Store post data
    
            par Notifications
                blog--)mail: Send mail to blog subscribers
                blog--)db: Store in-site notifications
            and Response
                blog-->>-web: Successfully posted
            end
        end
```
