## 📌 Aperçu du Projet
Base de données relationnelle analysant les caractéristiques des tueurs en série les plus prolifiques mondialement. Contient 34 cas documentés avec leurs méthodes, localisations et données judiciaires.

## 🗃️ Sources des Données
- **Dataset original** : [Serial Killers Dataset sur Kaggle](https://www.kaggle.com/datasets/vesuvius13/serial-killers-dataset?resource=download)
- **Fichier source** : [Highest_victim_count.csv](Highest_victim_count.csv)
- **Données complémentaires** : Enrichies manuellement par des données fictives 

## 🛠️ Structure Technique

### Diagramme Entité-Relation

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
