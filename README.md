```mermaid
flowchart TD
    A["Start: Data Pipeline Setup"] --> B1["Prerequisites"] & C["Configure Cortex XDR"] & D["Configure Logstash"] & E["Start Logstash"] & F["Validate Data Flow"]
    B1 --> B2["Ensure Cortex XDR Access"] & B3["Install and Configure Logstash"] & B4["Obtain Azure AD Credentials for ADX"] & B5["Ensure Network Connectivity"]
    C --> C1["Log in to Cortex XDR Console"]
    C1 --> C2["Navigate to Settings > Data Management > Data Export"]
    C2 --> C3["Add Data Export Configuration"]
    C3 --> C3a["Define Name, Type, Format, Destination URL"] & C3b["Configure Authentication if needed"] & C3c["Enable and Save Export"]
    D --> D1["Create Configuration File"] & D3["Optional: Add Filter Plugin"] & D4["Define Output Plugin for ADX"] & D5["Save Configuration"]
    D1 --> D2["Define Input Plugin: HTTP, Port, Codec"] & D2a["Example Config: input http port"]
    D3 --> D3a["Filter Plugin Example: json"]
    D4 --> D4a["Output Config: HTTP, URL, Headers, Mapping"]
    E --> E1["Command: bin/logstash -f cortex_xdr.conf"] & E2["Monitor Logstash Logs"]
    F --> F1["Check Cortex XDR Export Logs"] & F2["Verify Logstash Logs"] & F3["Run SQL Query in ADX: SELECT TOP 10 FROM CortexXDR"] & G["Success: Pipeline Operational"]
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style G fill:#bbf,stroke:#333,stroke-width:2px
