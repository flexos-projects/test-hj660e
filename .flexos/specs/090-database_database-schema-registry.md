---
type: spec
subtype: database-schema
title: Database Schema Registry
---

This document provides a detailed specification for the database schema, derived from the "Content & Data Models" document. It defines all tables, fields, data types, and relationships necessary to power the ISC website.

---

### Core Tables

#### `products`

Stores information about core ISC products like BIND 9 and Kea.

| Field Name           | Data Type         | Constraints / Notes                                    | Relationship                    |
| -------------------- | ----------------- | ------------------------------------------------------ | ------------------------------- |
| **`id`**             | `SERIAL`          | `PRIMARY KEY`                                          |                                 |
| `name`               | `VARCHAR(255)`    | `NOT NULL`                                             |                                 |
| `slug`               | `VARCHAR(255)`    | `UNIQUE`, `NOT NULL`                                   |                                 |
| `tagline`            | `TEXT`            |                                                        |                                 |
| `logo_id`            | `INTEGER`         | `NULLABLE`                                             | `media.id` (Foreign Key)        |
| `summary`            | `TEXT`            |                                                        |                                 |
| `body`               | `TEXT`            | Stores Markdown content                                |                                 |
| `download_link`      | `VARCHAR(2048)`   |                                                        |                                 |
| `documentation_link` | `VARCHAR(2048)`   |                                                        |                                 |
| `created_at`         | `TIMESTAMPTZ`     | `DEFAULT NOW()`                                        |                                 |
| `updated_at`         | `TIMESTAMPTZ`     | `DEFAULT NOW()`                                        |                                 |

#### `services`

Stores information about ISC's enterprise services.

| Field Name          | Data Type       | Constraints / Notes        | Relationship             |
| ------------------- | --------------- | -------------------------- | ------------------------ |
| **`id`**            | `SERIAL`        | `PRIMARY KEY`              |                          |
| `title`             | `VARCHAR(255)`  | `NOT NULL`                 |                          |
| `slug`              | `VARCHAR(255)`  | `UNIQUE`, `NOT NULL`       |                          |
| `summary`           | `TEXT`          |                            |                          |
| `body`              | `TEXT`          | Stores Markdown content    |                          |
| `audience_tag_id`   | `INTEGER`       | Pre-set to "Enterprise" tag | `tags.id` (Foreign Key) |
| `cta_label`         | `VARCHAR(255)`  |                            |                          |
| `cta_link`          | `VARCHAR(2048)` |                            |                          |
| `created_at`        | `TIMESTAMPTZ`   | `DEFAULT NOW()`            |                          |
| `updated_at`        | `TIMESTAMPTZ`   | `DEFAULT NOW()`            |                          |

#### `team_members`

Stores profiles for ISC experts.

| Field Name   | Data Type     | Constraints / Notes     | Relationship             |
| ------------ | ------------- | ----------------------- | ------------------------ |
| **`id`**     | `SERIAL`      | `PRIMARY KEY`           |                          |
| `name`       | `VARCHAR(255)`| `NOT NULL`              |                          |
| `title`      | `VARCHAR(255)`|                         |                          |
| `photo_id`   | `INTEGER`     | `NULLABLE`              | `media.id` (Foreign Key) |
| `bio`        | `TEXT`        | Stores Markdown content |                          |
| `is_active`  | `BOOLEAN`     | `DEFAULT TRUE`          |                          |
| `created_at` | `TIMESTAMPTZ` | `DEFAULT NOW()`         |                          |
| `updated_at` | `TIMESTAMPTZ` | `DEFAULT NOW()`         |                          |

#### `resources`

The core table for all content in the Knowledge Hub and Documentation sections.

| Field Name           | Data Type       | Constraints / Notes                                      | Relationship                  |
| -------------------- | --------------- | -------------------------------------------------------- | ----------------------------- |
| **`id`**             | `SERIAL`        | `PRIMARY KEY`                                            |                               |
| `title`              | `VARCHAR(255)`  | `NOT NULL`                                               |                               |
| `slug`               | `VARCHAR(255)`  | `UNIQUE`, `NOT NULL`, Auto-generated from title        |                               |
| `resource_type`      | `VARCHAR(50)`   | `CHECK IN ('Documentation', 'Knowledge Base Article', 'Announcement')` |                               |
| `author_id`          | `INTEGER`       | `NULLABLE`                                               | `team_members.id` (Foreign Key) |
| `publish_date`       | `TIMESTAMPTZ`   | `NOT NULL`                                               |                               |
| `body`               | `TEXT`          | Stores Markdown content                                  |                               |
| `related_product_id` | `INTEGER`       | `NULLABLE`                                               | `products.id` (Foreign Key)   |
| `product_version`    | `VARCHAR(50)`   | e.g., "9.18.1"                                           |                               |
| `created_at`         | `TIMESTAMPTZ`   | `DEFAULT NOW()`                                          |                               |
| `updated_at`         | `TIMESTAMPTZ`   | `DEFAULT NOW()`                                          |                               |

#### `testimonials`

Stores customer testimonials for social proof.

| Field Name        | Data Type      | Constraints / Notes | Relationship             |
| ----------------- | -------------- | ------------------- | ------------------------ |
| **`id`**          | `SERIAL`       | `PRIMARY KEY`       |                          |
| `quote`           | `TEXT`         | `NOT NULL`          |                          |
| `author_name`     | `VARCHAR(255)` | `NOT NULL`          |                          |
| `author_title`    | `VARCHAR(255)` |                     |                          |
| `company_name`    | `VARCHAR(255)` |                     |                          |
| `company_logo_id` | `INTEGER`      | `NULLABLE`          | `media.id` (Foreign Key) |
| `is_featured`     | `BOOLEAN`      | `DEFAULT FALSE`     |                          |
| `created_at`      | `TIMESTAMPTZ`  | `DEFAULT NOW()`     |                          |
| `updated_at`      | `TIMESTAMPTZ`  | `DEFAULT NOW()`     |                          |

#### `site_globals`

A singleton table for site-wide configuration. This table must only ever contain one row.

| Field Name                        | Data Type      | Constraints / Notes                      | Relationship |
| --------------------------------- | -------------- | ---------------------------------------- | ------------ |
| **`id`**                          | `INTEGER`      | `PRIMARY KEY`, `CHECK (id = 1)`          |              |
| `site_name`                       | `VARCHAR(255)` |                                          |              |
| `site_tagline`                    | `TEXT`         |                                          |              |
| `contact_email_sales`             | `VARCHAR(255)` |                                          |              |
| `contact_email_general`           | `VARCHAR(255)` |                                          |              |
| `security_contact_instructions`   | `TEXT`         | Stores Markdown content                  |              |
| `updated_at`                      | `TIMESTAMPTZ`  | `DEFAULT NOW()`                          |              |

---

### Relational & Supporting Tables

#### `product_features`

A "repeater" table to store a list of features for each product.

| Field Name            | Data Type      | Constraints / Notes | Relationship              |
| --------------------- | -------------- | ------------------- | ------------------------- |
| **`id`**              | `SERIAL`       | `PRIMARY KEY`       |                           |
| `product_id`          | `INTEGER`      | `NOT NULL`          | `products.id` (Foreign Key) |
| `icon`                | `VARCHAR(100)` | Icon identifier     |                           |
| `feature_title`       | `VARCHAR(255)` | `NOT NULL`          |                           |
| `feature_description` | `TEXT`         |                     |                           |

#### `team_member_social_links`

A "repeater" table to store social media links for each team member.

| Field Name        | Data Type       | Constraints / Notes                         | Relationship                  |
| ----------------- | --------------- | ------------------------------------------- | ----------------------------- |
| **`id`**          | `SERIAL`        | `PRIMARY KEY`                               |                               |
| `team_member_id`  | `INTEGER`       | `NOT NULL`                                  | `team_members.id` (Foreign Key) |
| `platform`        | `VARCHAR(50)`   | `CHECK IN ('LinkedIn', 'Twitter', 'GitHub')`|                               |
| `url`             | `VARCHAR(2048)` | `NOT NULL`                                  |                               |

#### `site_globals_social_links`

A "repeater" table to store site-wide social media links.

| Field Name        | Data Type       | Constraints / Notes | Relationship                  |
| ----------------- | --------------- | ------------------- | ----------------------------- |
| **`id`**          | `SERIAL`        | `PRIMARY KEY`       |                               |
| `site_globals_id` | `INTEGER`       | `NOT NULL`          | `site_globals.id` (Foreign Key) |
| `platform`        | `VARCHAR(100)`  | e.g., "LinkedIn"    |                               |
| `url`             | `VARCHAR(2048)` | `NOT NULL`          |                               |

#### `tags`

A central table for all tags used across the site (e.g., for resources, services).

| Field Name | Data Type      | Constraints / Notes  | Relationship |
| ---------- | -------------- | -------------------- | ------------ |
| **`id`**   | `SERIAL`       | `PRIMARY KEY`        |              |
| `name`     | `VARCHAR(100)` | `UNIQUE`, `NOT NULL` |              |
| `slug`     | `VARCHAR(100)` | `UNIQUE`, `NOT NULL` |              |

#### `resource_tags` (Join Table)

Links resources to tags in a many-to-many relationship.

| Field Name      | Data Type | Constraints / Notes             | Relationship              |
| --------------- | --------- | ------------------------------- | ------------------------- |
| **`resource_id`** | `INTEGER` | `PRIMARY KEY`, `NOT NULL`       | `resources.id` (Foreign Key) |
| **`tag_id`**      | `INTEGER` | `PRIMARY KEY`, `NOT NULL`       | `tags.id` (Foreign Key)      |

#### `media`

A central repository for all media assets like images and logos.

| Field Name   | Data Type       | Constraints / Notes | Relationship |
| ------------ | --------------- | ------------------- | ------------ |
| **`id`**     | `SERIAL`        | `PRIMARY KEY`       |              |
| `url`        | `VARCHAR(2048)` | `NOT NULL`          |              |
| `alt_text`   | `TEXT`          |                     |              |
| `mime_type`  | `VARCHAR(100)`  |                     |              |
| `created_at` | `TIMESTAMPTZ`   | `DEFAULT NOW()`     |              |