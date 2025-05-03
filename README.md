```mermaid
erDiagram
    serial_killers ||--o{ methods : "1-N"
    serial_killers ||--|| locations : "1-1"
    serial_killers ||--|| investigations : "1-1"
    
    serial_killers {
        integer killer_id PK
        text name
        integer start_year
        text country
    }
    
    methods {
        integer method_id PK
        integer killer_id FK
        text method_name
    }
    
    locations {
        integer location_id PK
        integer killer_id FK
        decimal crime_rate
    }
