erDiagram
    %% Requirements Management Database Schema
    
    requirements ||--o{ requirement_versions : "has"
    requirements ||--o{ sub_requirements : "has"
    requirements ||--o{ validation_rules : "contains"
    requirements ||--o{ code_blocks : "implements"
    requirements ||--o{ requirement_stakeholders : "owned by"
    requirements ||--o{ traceability : "relates to"
    
    requirement_versions ||--o{ requirement_metadata : "describes"
    requirement_versions ||--o{ data_lineage : "flows through"
    
    stakeholders ||--o{ requirement_stakeholders : "responsible for"
    
    policies ||--o{ requirement_policies : "governs"
    standards ||--o{ requirement_policies : "references"
    
    requirements ||--o{ requirement_policies : "complies with"
    
    sdlc_phases ||--o{ requirement_sdlc_mapping : "tracks"
    requirements ||--o{ requirement_sdlc_mapping : "progresses through"
    
    data_lineage ||--o{ data_lineage_edges : "connects"
    data_sources ||--o{ data_lineage : "provides"
    
    users ||--o{ user_permissions : "has access"
    requirements ||--o{ user_permissions : "secured by"
    
    requirements {
        varchar requirement_id PK
        varchar title
        text summary
        varchar status
        varchar priority
        varchar rfc_level
    }
    
    sub_requirements {
        varchar sub_requirement_id PK
        varchar requirement_id FK
        varchar sub_title
        text sub_summary
        varchar sub_status
        int sequence_number
    }
    
    requirement_versions {
        int version_id PK
        varchar requirement_id FK
        varchar version_number
        varchar version_status
        date release_date
    }
    
    requirement_metadata {
        int metadata_id PK
        int version_id FK
        text business_value
        text technical_impact
    }
    
    validation_rules {
        int rule_id PK
        varchar requirement_id FK
        varchar rule_category
        text rule_text
    }
    
    code_blocks {
        int code_id PK
        varchar requirement_id FK
        varchar code_type
        text code_content
    }
    
    stakeholders {
        int stakeholder_id PK
        varchar name
        varchar email
        varchar role
    }
    
    requirement_stakeholders {
        int mapping_id PK
        varchar requirement_id FK
        int stakeholder_id FK
        varchar responsibility_type
    }
    
    policies {
        varchar policy_id PK
        varchar policy_name
    }
    
    standards {
        varchar standard_id PK
        varchar standard_name
        varchar standard_body
    }
    
    requirement_policies {
        int mapping_id PK
        varchar requirement_id FK
        varchar policy_id FK
        varchar standard_id FK
    }
    
    sdlc_phases {
        int phase_id PK
        varchar phase_name
    }
    
    requirement_sdlc_mapping {
        int mapping_id PK
        varchar requirement_id FK
        int phase_id FK
        varchar phase_status
    }
    
    data_sources {
        int source_id PK
        varchar source_name
        varchar source_type
    }
    
    data_lineage {
        int lineage_id PK
        varchar requirement_id FK
        int source_id FK
        varchar node_type
    }
    
    data_lineage_edges {
        int edge_id PK
        int lineage_id_from FK
        int lineage_id_to FK
    }
    
    users {
        int user_id PK
        varchar username
        varchar role
    }
    
    user_permissions {
        int permission_id PK
        int user_id FK
        varchar requirement_id FK
        varchar permission_type
    }
    
    traceability {
        int trace_id PK
        varchar requirement_id_from FK
        varchar requirement_id_to FK
        varchar relationship_type
    }