
dadad
ad
a
da
da


```mermaid
erDiagram
    serial_killers ||--o{ methods : "utilise"
    serial_killers ||--|| locations : "localisé dans"
    serial_killers ||--|| investigations : "fait l'objet"
   serial_killers {
        integer killer_id PK
        text name
        integer start_year
        integer end_year
        text years_active
        integer proven_victims
        text possible_victims
        text country
        integer birth_year
        text mental_health_diagnosis
        text status
        text keywords
    }

    methods {
        integer method_id PK
        integer killer_id FK
        text method_name
    }

    locations {
        integer location_id PK
        integer killer_id FK
        decimal poor_rate_of_the_country
        decimal crime_rate
        boolean legal_gun_ownership
        text country
        text city
    }

    investigations {
        integer investigation_id PK
        integer killer_id FK
        integer start_year
        integer end_year
        integer arrest_year
        integer conviction_year
        integer number_of_victims_confirmed
        integer number_of_victims_claimed
    }
