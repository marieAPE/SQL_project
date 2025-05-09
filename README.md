## 📌 Aperçu du Projet
Base de données relationnelle analysant les caractéristiques des tueurs en série les plus prolifiques mondialement. Contient 34 cas documentés avec leurs méthodes, localisations et données judiciaires. Cela a pour but, via des requêtes SQL, si y existe des corrélations entre plusieurs éléments, analyser l'impact d'un contexte socio-économique, faire des études sur l'éfficacité des enquêtes judiciaire ou encore bien-sûr obtenir des informations sur un ou plusieurs éléments en particulier (ex : un/plusieurs individu(s), un pays, une méthode, etc..) 

## 🗃️ Sources des Données
- **Dataset original** : [Serial Killers Dataset sur Kaggle](https://www.kaggle.com/datasets/vesuvius13/serial-killers-dataset?resource=download)
- **Fichier source** : [Highest_victim_count.csv](Highest_victim_count.csv)
- **Données complémentaires** : Enrichies manuellement par des données fictives 

## 📂 Fichiers du Projet
- [Document de conception](Document_de_conception.pdf) - Explication détaillée de la structure et des choix techniques
- [Script des requêtes SQL](Script_de_requetes) - Requêtes d'analyse prêtes à l'emploi
- [Script du schéma](Script_de_schema) - Code SQL pour recréer la structure de la base
- [Base de données complète](SQL_killers.db) - Fichier SQLite opérationnel


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
