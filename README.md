erDiagram
    ADDRESSES ||--o{ STAFF : has
    ADDRESSES ||--o{ CUSTOMER : has
    ADDRESSES ||--o{ Filial : has
    STAFF ||--o{ Filial : has
    STAFF ||--o{ RENT : has
    CUSTOMER ||--o{ RENT : has
    Filial ||--o{ VEHICLE : has
    COST ||--o{ VEHICLE : has
    VEHICLE ||--o{ RENT : has
    RENT ||--o{ PAYMENT : has

    ADDRESSES {
        serial address_id PK
        varchar street_name "NOT NULL"
        varchar house_number "NOT NULL"
        varchar city "NOT NULL"
        varchar country "NOT NULL"
        int zipcode "NOT NULL"
    }

    STAFF {
        serial staff_id PK
        varchar first_name "NOT NULL"
        varchar last_name "NOT NULL"
        date date_of_birth
        int filial_id "NOT NULL"
        numeric commission
        int address_id
    }

    CUSTOMER {
        serial customer_id PK
        varchar first_name "NOT NULL"
        varchar last_name "NOT NULL"
        date date_of_birth "NOT NULL"
        varchar license_number "NOT NULL"
        int address_id
    }

    Filial {
        serial branch_id PK
        int manager_id
        int address_id
    }

    COST {
        serial cost_id PK
        varchar cost_class "NOT NULL"
        numeric cost
        numeric cost_per_day
        numeric deposit
    }

    VEHICLE {
        serial vehicle_id PK
        varchar brand
        int mileage
        date date_bought
        int cost_id "NOT NULL"
        int Filial_id "NOT NULL"
        bool is_available "NOT NULL"
    }

    RENT {
        serial rent_id PK
        int vehicle_id "NOT NULL"
        int customer_id "NOT NULL"
        int staff_id "NOT NULL"
        date date_rented "NOT NULL"
    }

    PAYMENT {
        int rent_id PK, FK "NOT NULL"
        numeric payment_amount "NOT NULL"
        date payment_date PK "NOT NULL"
    }
