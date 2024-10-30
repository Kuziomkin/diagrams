```mermaid
---
config:
  layout: dagre
  look: classic
  theme: neutral
---
flowchart TD
    subgraph component diagram
        id1(System1)
        id2[(Database)]
        id3(System2)

        subgraph **_Component1_**
            id1 -.
                Name, 
                Id,
                Bill Information
            .-> id2
            id1 --> Junction
        end
    end
```

```mermaid
---
title: Node with text
config:
  layout: dagre
  look: classic
  theme: neutral
---
flowchart TD    
    A((Start)) --> B{Is it?}
    B -->|Yes| C[OK]
    C --> D[Rethink]
    C --> B
    D --> B
    B ---->|No| E((End))
```

```mermaid
---
title: Context Diagram
config:
  layout: dagre
  look: classic
  theme: neutral
---
    flowchart TD
        %% define components
        D[System D]
        E[System E]
        A(((System A)))
        B[System B]
        C[System C]

        subgraph " "
            %% define relationships
            E -- Booked Item --> A
            A -.Operation Result.-> E
            A --Get Client Information--> D
            D -.Information.- A
            A -- Get Catalog--> B
            B -. Catalog .-> A
            A --Process Transaction--> C
            C -.Process Result.->A
        end

```

