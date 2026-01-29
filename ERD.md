# Entity Relationship Diagram (ERD)

This diagram shows the data model for the Payment & Transaction Analytics project.

```mermaid
erDiagram
    USER {
        STRING user_id PK
        STRING user_name
        STRING email
        STRING country
    }

    MERCHANT {
        STRING merchant_id PK
        STRING merchant_name
        STRING category
        STRING country
    }

    PAYMENT_METHOD {
        STRING payment_method_id PK
        STRING method_name
        STRING provider
    }

    TRANSACTION {
        STRING transaction_id PK
        STRING user_id FK
        STRING merchant_id FK
        STRING payment_method_id FK
        DECIMAL amount
        DECIMAL fee
        STRING currency
        STRING status
        TIMESTAMP created_at
        TIMESTAMP settled_at
    }

    USER ||--o{ TRANSACTION : makes
    MERCHANT ||--o{ TRANSACTION : receives
    PAYMENT_METHOD ||--o{ TRANSACTION : uses
