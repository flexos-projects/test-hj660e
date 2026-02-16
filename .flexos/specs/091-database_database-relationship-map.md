```yaml
---
type: spec
subtype: database-relationships
title: Database Relationship Map
---

This document provides a visual map of the relationships between the database tables defined in the Schema Registry. The diagram illustrates primary key (PK) and foreign key (FK) connections, as well as relationship cardinality (one-to-one, one-to-many, many-to-many).

### Entity Relationship Diagram (ERD)

```mermaid
erDiagram
    products {
        SERIAL id PK
        VARCHAR name
        VARCHAR slug
        INTEGER logo_id FK
        TEXT summary
        TEXT body
    }
    product_features {
        SERIAL id PK
        INTEGER product_id FK
        VARCHAR icon
        VARCHAR feature_title
        TEXT feature_description
    }
    services {
        SERIAL id PK
        VARCHAR title
        VARCHAR slug
        INTEGER audience_tag_id FK
        TEXT body
    }
    team_members {
        SERIAL id PK
        VARCHAR name
        VARCHAR title
        INTEGER photo_id FK
        TEXT bio
        BOOLEAN is_active
    }
    team_member_social_links {
        SERIAL id PK
        INTEGER team_member_id FK
        VARCHAR platform
        VARCHAR url
    }
    resources {
        SERIAL id PK
        VARCHAR title
        VARCHAR slug
        INTEGER author_id FK
        DATETIME publish_date
        INTEGER related_product_id FK
    }
    tags {
        SERIAL id PK
        VARCHAR name
        VARCHAR slug
    }
    resource_tags {
        INTEGER resource_id PK,FK
        INTEGER tag_id PK,FK
    }
    testimonials {
        SERIAL id PK
        TEXT quote
        VARCHAR author_name
        INTEGER company_logo_id FK
        BOOLEAN is_featured
    }
    site_globals {
        INTEGER id PK
        VARCHAR site_name
        TEXT site_tagline
    }
    site_globals_social_links {
        SERIAL id PK
        INTEGER site_globals_id FK
        VARCHAR platform
        VARCHAR url
    }
    media {
        SERIAL id PK
        VARCHAR url
        TEXT alt_text
    }

    products ||--|{ product_features : "has"
    products }o--|| resources : "is related to"
    products }o--|| media : "has logo"

    team_members }o--|| media : "has photo"
    team_members ||--|{ team_member_social_links : "has"
    team_members }o--|| resources : "authored by"

    services }o--|| tags : "has audience"

    resources ||--|{ resource_tags : "has"
    tags      ||--|{ resource_tags : "is on"

    testimonials }o--o| media : "has logo (optional)"

    site_globals ||--|{ site_globals_social_links : "has"