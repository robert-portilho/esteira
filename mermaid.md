flowchart LR

    subgraph APPS["Namespaces Kubernetes"]
        subgraph N1["Namespace A"]
            A1["Apps"]
            C1["Collector A"]
        end

        subgraph N2["Namespace B"]
            A2["Apps"]
            C2["Collector B"]
        end
    end

    subgraph DATA["Canal de Dados de Negócio"]
        K["Kafka"]
    end

    subgraph NODE["Camada Node (DaemonSet)"]
        D["OTel Collector DaemonSet"]
    end

    subgraph GATEWAY["Camada Gateway"]
        G["OTel Collector Gateway"]
    end

    subgraph BACKENDS["Observabilidade"]
        M["Metrics"]
        T["Traces"]
        L["Logs Técnicos"]
    end

    A1 --> C1
    A2 --> C2

    C1 -->|Metrics| D
    C1 -->|Traces| D
    C1 -->|Logs Técnicos| D

    C2 -->|Metrics| D
    C2 -->|Traces| D
    C2 -->|Logs Técnicos| D

    C1 -.->|Logs Negócio| K
    C2 -.->|Logs Negócio| K

    D --> G

    G --> M
    G --> T
    G --> L

    style K fill:#fff3cd,stroke:#ff9800,stroke-width:3px
    style D fill:#e3f2fd
    style G fill:#bbdefb
