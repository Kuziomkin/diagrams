```mermaid
---
config:
  layout: dagre
  look: classic
  theme: neutral
---
flowchart TD 
    a[Default]
    b([Rounded])
    c[(Database)]
    d[[Subroutine]]
    e((Circle))
    f>Note]
    g{Decision}
    h{{Hexagon}}
    i[/Parallelogram/]
    j(((Double Circle)))
```
----

```mermaid
---
config:
  layout: dagre
  look: classic
  theme: neutral
---
flowchart LR
    subgraph Azure
        s[fa:fa-code Server]
        db[(fa:fa-table Database)]
    end
    subgraph Netlify
        c[fa:fa-user Client]
    end

    subgraph Netlify
    end
    subgraph Azure
        direction LR
    end
    
    c -- HTTP GET --> s
    s -- SQL Query --> db
    db -. Result Set .-> s
    s -. JSON .-> c
```

```mermaid
---
title: Use Case Diagram
config:
  layout: dagre
  look: classic
  theme: neutral
---
    flowchart LR
        %% define components
        A[/fa:fa-user Actor\]

        subgraph " "
            direction LR
            L([Login])
            G([See Places])
            B([Book Place])
        end

        %% define relationships
        A --> L
        A --> G
        G -.Extend.-> B
        B -.Use.-> L
```



