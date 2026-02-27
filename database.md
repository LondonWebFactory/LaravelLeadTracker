# Relaticle Database Dictionary

Generated: 2026-02-27 08:49:54

## ai_summaries

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| summarizable_type | varchar | NO |  |
| summarizable_id | varchar | NO |  |
| summary | TEXT | NO |  |
| model_used | varchar | NO |  |
| prompt_tokens | INTEGER | YES |  |
| completion_tokens | INTEGER | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## cache

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| key | varchar | NO |  |
| value | TEXT | NO |  |
| expiration | INTEGER | NO |  |

---

## cache_locks

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| key | varchar | NO |  |
| owner | varchar | NO |  |
| expiration | INTEGER | NO |  |

---

## companies

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| creator_id | varchar | YES |  |
| account_owner_id | varchar | YES |  |
| name | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| deleted_at | datetime | YES |  |
| creation_source | varchar | NO |  |

---

## custom_field_options

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| tenant_id | varchar | YES |  |
| custom_field_id | varchar | NO |  |
| name | varchar | YES |  |
| sort_order | INTEGER | YES |  |
| settings | TEXT | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## custom_field_sections

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| tenant_id | varchar | YES |  |
| width | varchar | YES |  |
| code | varchar | NO |  |
| name | varchar | NO |  |
| type | varchar | NO |  |
| entity_type | varchar | NO |  |
| sort_order | INTEGER | YES |  |
| description | varchar | YES |  |
| active | tinyint(1) | NO | '1' |
| system_defined | tinyint(1) | NO | '0' |
| settings | TEXT | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## custom_field_values

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| tenant_id | varchar | YES |  |
| entity_type | varchar | NO |  |
| entity_id | varchar | NO |  |
| custom_field_id | varchar | NO |  |
| string_value | TEXT | YES |  |
| text_value | TEXT | YES |  |
| boolean_value | tinyint(1) | YES |  |
| integer_value | INTEGER | YES |  |
| float_value | double | YES |  |
| date_value | date | YES |  |
| datetime_value | datetime | YES |  |
| json_value | TEXT | YES |  |

---

## custom_fields

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| custom_field_section_id | varchar | YES |  |
| width | varchar | YES |  |
| tenant_id | varchar | YES |  |
| code | varchar | NO |  |
| name | varchar | NO |  |
| type | varchar | NO |  |
| lookup_type | varchar | YES |  |
| entity_type | varchar | NO |  |
| sort_order | INTEGER | YES |  |
| validation_rules | TEXT | YES |  |
| active | tinyint(1) | NO | '1' |
| system_defined | tinyint(1) | NO | '0' |
| settings | TEXT | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## exports

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | YES |  |
| completed_at | datetime | YES |  |
| file_disk | varchar | NO |  |
| file_name | varchar | YES |  |
| exporter | varchar | NO |  |
| processed_rows | INTEGER | NO | '0' |
| total_rows | INTEGER | NO |  |
| successful_rows | INTEGER | NO | '0' |
| user_id | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## failed_import_rows

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | YES |  |
| data | TEXT | NO |  |
| import_id | varchar | NO |  |
| validation_error | TEXT | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## failed_jobs

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| uuid | varchar | NO |  |
| connection | TEXT | NO |  |
| queue | TEXT | NO |  |
| payload | TEXT | NO |  |
| exception | TEXT | NO |  |
| failed_at | datetime | NO | CURRENT_TIMESTAMP |

---

## imports

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | YES |  |
| completed_at | datetime | YES |  |
| file_name | varchar | NO |  |
| total_rows | INTEGER | NO |  |
| user_id | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| entity_type | varchar | YES |  |
| status | varchar | NO | 'uploading' |
| headers | TEXT | YES |  |
| column_mappings | TEXT | YES |  |
| created_rows | INTEGER | NO | '0' |
| updated_rows | INTEGER | NO | '0' |
| skipped_rows | INTEGER | NO | '0' |
| failed_rows | INTEGER | NO | '0' |

---

## job_batches

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| name | varchar | NO |  |
| total_jobs | INTEGER | NO |  |
| pending_jobs | INTEGER | NO |  |
| failed_jobs | INTEGER | NO |  |
| failed_job_ids | TEXT | NO |  |
| options | TEXT | YES |  |
| cancelled_at | INTEGER | YES |  |
| created_at | INTEGER | NO |  |
| finished_at | INTEGER | YES |  |

---

## jobs

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| queue | varchar | NO |  |
| payload | TEXT | NO |  |
| attempts | INTEGER | NO |  |
| reserved_at | INTEGER | YES |  |
| available_at | INTEGER | NO |  |
| created_at | INTEGER | NO |  |

---

## media

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| model_type | varchar | NO |  |
| model_id | varchar | NO |  |
| uuid | varchar | YES |  |
| collection_name | varchar | NO |  |
| name | varchar | NO |  |
| file_name | varchar | NO |  |
| mime_type | varchar | YES |  |
| disk | varchar | NO |  |
| conversions_disk | varchar | YES |  |
| size | INTEGER | NO |  |
| manipulations | TEXT | NO |  |
| custom_properties | TEXT | NO |  |
| generated_conversions | TEXT | NO |  |
| responsive_images | TEXT | NO |  |
| order_column | INTEGER | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## migrations

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| migration | varchar | NO |  |
| batch | INTEGER | NO |  |

---

## noteables

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| note_id | varchar | NO |  |
| noteable_type | varchar | NO |  |
| noteable_id | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## notes

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| creator_id | varchar | YES |  |
| title | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| deleted_at | datetime | YES |  |
| creation_source | varchar | NO |  |

---

## notifications

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| type | varchar | NO |  |
| notifiable_type | varchar | NO |  |
| notifiable_id | varchar | NO |  |
| data | TEXT | NO |  |
| read_at | datetime | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## opportunities

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| creator_id | varchar | YES |  |
| company_id | varchar | YES |  |
| contact_id | varchar | YES |  |
| name | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| deleted_at | datetime | YES |  |
| creation_source | varchar | NO |  |
| order_column | numeric | YES |  |

---

## password_reset_tokens

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| email | varchar | NO |  |
| token | varchar | NO |  |
| created_at | datetime | YES |  |

---

## people

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| creator_id | varchar | YES |  |
| company_id | varchar | YES |  |
| name | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| deleted_at | datetime | YES |  |
| creation_source | varchar | NO |  |

---

## personal_access_tokens

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| tokenable_type | varchar | NO |  |
| tokenable_id | varchar | NO |  |
| name | varchar | NO |  |
| token | varchar | NO |  |
| abilities | TEXT | YES |  |
| last_used_at | datetime | YES |  |
| expires_at | datetime | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## sessions

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| user_id | varchar | YES |  |
| ip_address | varchar | YES |  |
| user_agent | TEXT | YES |  |
| payload | TEXT | NO |  |
| last_activity | INTEGER | NO |  |

---

## system_administrators

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| name | varchar | NO |  |
| email | varchar | NO |  |
| email_verified_at | datetime | YES |  |
| password | varchar | NO |  |
| role | varchar | NO |  |
| remember_token | varchar | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## task_user

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| task_id | varchar | NO |  |
| user_id | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## taskables

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| task_id | varchar | NO |  |
| taskable_type | varchar | NO |  |
| taskable_id | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## tasks

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| creator_id | varchar | YES |  |
| title | varchar | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| deleted_at | datetime | YES |  |
| creation_source | varchar | NO |  |
| order_column | numeric | YES |  |

---

## team_invitations

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| team_id | varchar | NO |  |
| email | varchar | NO |  |
| role | varchar | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## team_user

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | INTEGER | NO |  |
| team_id | varchar | NO |  |
| user_id | varchar | NO |  |
| role | varchar | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## teams

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| user_id | varchar | NO |  |
| name | varchar | NO |  |
| personal_team | tinyint(1) | NO |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| slug | varchar | NO |  |

---

## user_social_accounts

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| user_id | varchar | NO |  |
| provider_name | varchar | YES |  |
| provider_id | varchar | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |

---

## users

| Column | Type | Nullable | Default |
|--------|------|----------|---------|
| id | varchar | NO |  |
| name | varchar | NO |  |
| email | varchar | NO |  |
| email_verified_at | datetime | YES |  |
| password | varchar | YES |  |
| remember_token | varchar | YES |  |
| current_team_id | varchar | YES |  |
| profile_photo_path | varchar | YES |  |
| created_at | datetime | YES |  |
| updated_at | datetime | YES |  |
| two_factor_secret | TEXT | YES |  |
| two_factor_recovery_codes | TEXT | YES |  |
| two_factor_confirmed_at | datetime | YES |  |

---

