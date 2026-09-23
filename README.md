# Azure Secure Network Architecture
Cloud infrastructure project implementing networking principles, Network Security Groups, and secure Service Endpoints on Azure.

```mermaid
graph TD
    subgraph Internet
        User[Local Machine / Admin]
    end

    User -->|Port 22 SSH| PIP[Public IP: 20.230.184.67]

    subgraph VNetA ["VNet A (10.0.0.0/16)"]
        direction TB
        
        subgraph SubnetA ["Subnet-A (10.0.0.0/24) + NSG"]
            PIP --> NIC[VM1 (Ubuntu)]
        end
        
        %% This invisible link forces the VNet box to expand wider than the subnet box
        SubnetA ~~~ VNetPadding[ ]
    end

    SubnetA -.->|Subnet Service Endpoint| SQL[Azure SQL Database<br/>- Public Access: Disabled]

    style VNetA fill:none,stroke:#333,stroke-width:2px
    style SubnetA fill:#e1f5fe,stroke:#01579b,stroke-width:1px
    style VNetPadding display:none
```
