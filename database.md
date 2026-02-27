# Relaticle Database Dictionary

Generated: 2026-02-27 09:45:00
Connection: sqlite

## ai_summaries

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| summarizable_type | varchar | NO |  |  |
| summarizable_id | varchar | NO |  |  |
| summary | TEXT | NO |  |  |
| model_used | varchar | NO |  |  |
| prompt_tokens | INTEGER | YES |  |  |
| completion_tokens | INTEGER | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- ai_summaries.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **ai_summaries_summarizable_type_summarizable_id_team_id_unique** (UNIQUE) on `summarizable_type, summarizable_id, team_id`
- **ai_summaries_summarizable_type_summarizable_id_index** (NON-UNIQUE) on `summarizable_type, summarizable_id`
- **sqlite_autoindex_ai_summaries_1** (UNIQUE) on `id`

---

## cache

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| key | varchar | NO |  | YES |
| value | TEXT | NO |  |  |
| expiration | INTEGER | NO |  |  |

### Relationships

- *(none)*

### Indexes

- **sqlite_autoindex_cache_1** (UNIQUE) on `key`

---

## cache_locks

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| key | varchar | NO |  | YES |
| owner | varchar | NO |  |  |
| expiration | INTEGER | NO |  |  |

### Relationships

- *(none)*

### Indexes

- **sqlite_autoindex_cache_locks_1** (UNIQUE) on `key`

---

## companies

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| creator_id | varchar | YES |  |  |
| account_owner_id | varchar | YES |  |  |
| name | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| deleted_at | datetime | YES |  |  |
| creation_source | varchar | NO |  |  |

### Relationships

- companies.account_owner_id → users.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- companies.creator_id → users.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- companies.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_companies_1** (UNIQUE) on `id`

---

## custom_field_options

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| tenant_id | varchar | YES |  |  |
| custom_field_id | varchar | NO |  |  |
| name | varchar | YES |  |  |
| sort_order | INTEGER | YES |  |  |
| settings | TEXT | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- custom_field_options.custom_field_id → custom_fields.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **custom_field_options_tenant_id_index** (NON-UNIQUE) on `tenant_id`
- **custom_field_options_custom_field_id_name_tenant_id_unique** (UNIQUE) on `custom_field_id, name, tenant_id`
- **sqlite_autoindex_custom_field_options_1** (UNIQUE) on `id`

---

## custom_field_sections

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| tenant_id | varchar | YES |  |  |
| width | varchar | YES |  |  |
| code | varchar | NO |  |  |
| name | varchar | NO |  |  |
| type | varchar | NO |  |  |
| entity_type | varchar | NO |  |  |
| sort_order | INTEGER | YES |  |  |
| description | varchar | YES |  |  |
| active | tinyint(1) | NO | '1' |  |
| system_defined | tinyint(1) | NO | '0' |  |
| settings | TEXT | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **custom_field_sections_tenant_id_index** (NON-UNIQUE) on `tenant_id`
- **custom_field_sections_tenant_entity_active_idx** (NON-UNIQUE) on `tenant_id, entity_type, active`
- **custom_field_sections_entity_type_code_tenant_id_unique** (UNIQUE) on `entity_type, code, tenant_id`
- **sqlite_autoindex_custom_field_sections_1** (UNIQUE) on `id`

---

## custom_field_values

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| tenant_id | varchar | YES |  |  |
| entity_type | varchar | NO |  |  |
| entity_id | varchar | NO |  |  |
| custom_field_id | varchar | NO |  |  |
| string_value | TEXT | YES |  |  |
| text_value | TEXT | YES |  |  |
| boolean_value | tinyint(1) | YES |  |  |
| integer_value | INTEGER | YES |  |  |
| float_value | double | YES |  |  |
| date_value | date | YES |  |  |
| datetime_value | datetime | YES |  |  |
| json_value | TEXT | YES |  |  |

### Relationships

- custom_field_values.custom_field_id → custom_fields.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **custom_field_values_tenant_id_index** (NON-UNIQUE) on `tenant_id`
- **custom_field_values_entity_id_custom_field_id_index** (NON-UNIQUE) on `entity_id, custom_field_id`
- **custom_field_values_tenant_entity_idx** (NON-UNIQUE) on `tenant_id, entity_type, entity_id`
- **custom_field_values_entity_type_unique** (UNIQUE) on `entity_type, entity_id, custom_field_id, tenant_id`
- **custom_field_values_entity_type_entity_id_index** (NON-UNIQUE) on `entity_type, entity_id`
- **sqlite_autoindex_custom_field_values_1** (UNIQUE) on `id`

---

## custom_fields

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| custom_field_section_id | varchar | YES |  |  |
| width | varchar | YES |  |  |
| tenant_id | varchar | YES |  |  |
| code | varchar | NO |  |  |
| name | varchar | NO |  |  |
| type | varchar | NO |  |  |
| lookup_type | varchar | YES |  |  |
| entity_type | varchar | NO |  |  |
| sort_order | INTEGER | YES |  |  |
| validation_rules | TEXT | YES |  |  |
| active | tinyint(1) | NO | '1' |  |
| system_defined | tinyint(1) | NO | '0' |  |
| settings | TEXT | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **custom_fields_tenant_id_index** (NON-UNIQUE) on `tenant_id`
- **custom_fields_tenant_entity_active_idx** (NON-UNIQUE) on `tenant_id, entity_type, active`
- **custom_fields_code_entity_type_tenant_id_unique** (UNIQUE) on `code, entity_type, tenant_id`
- **sqlite_autoindex_custom_fields_1** (UNIQUE) on `id`

---

## exports

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | YES |  |  |
| completed_at | datetime | YES |  |  |
| file_disk | varchar | NO |  |  |
| file_name | varchar | YES |  |  |
| exporter | varchar | NO |  |  |
| processed_rows | INTEGER | NO | '0' |  |
| total_rows | INTEGER | NO |  |  |
| successful_rows | INTEGER | NO | '0' |  |
| user_id | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- exports.user_id → users.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*
- exports.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_exports_1** (UNIQUE) on `id`

---

## failed_import_rows

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | YES |  |  |
| data | TEXT | NO |  |  |
| import_id | varchar | NO |  |  |
| validation_error | TEXT | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- failed_import_rows.import_id → imports.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*
- failed_import_rows.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_failed_import_rows_1** (UNIQUE) on `id`

---

## failed_jobs

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| uuid | varchar | NO |  |  |
| connection | TEXT | NO |  |  |
| queue | TEXT | NO |  |  |
| payload | TEXT | NO |  |  |
| exception | TEXT | NO |  |  |
| failed_at | datetime | NO | CURRENT_TIMESTAMP |  |

### Relationships

- *(none)*

### Indexes

- **failed_jobs_uuid_unique** (UNIQUE) on `uuid`

---

## imports

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | YES |  |  |
| completed_at | datetime | YES |  |  |
| file_name | varchar | NO |  |  |
| total_rows | INTEGER | NO |  |  |
| user_id | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| entity_type | varchar | YES |  |  |
| status | varchar | NO | 'uploading' |  |
| headers | TEXT | YES |  |  |
| column_mappings | TEXT | YES |  |  |
| created_rows | INTEGER | NO | '0' |  |
| updated_rows | INTEGER | NO | '0' |  |
| skipped_rows | INTEGER | NO | '0' |  |
| failed_rows | INTEGER | NO | '0' |  |

### Relationships

- imports.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*
- imports.user_id → users.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_imports_1** (UNIQUE) on `id`

---

## job_batches

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| name | varchar | NO |  |  |
| total_jobs | INTEGER | NO |  |  |
| pending_jobs | INTEGER | NO |  |  |
| failed_jobs | INTEGER | NO |  |  |
| failed_job_ids | TEXT | NO |  |  |
| options | TEXT | YES |  |  |
| cancelled_at | INTEGER | YES |  |  |
| created_at | INTEGER | NO |  |  |
| finished_at | INTEGER | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **sqlite_autoindex_job_batches_1** (UNIQUE) on `id`

---

## jobs

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| queue | varchar | NO |  |  |
| payload | TEXT | NO |  |  |
| attempts | INTEGER | NO |  |  |
| reserved_at | INTEGER | YES |  |  |
| available_at | INTEGER | NO |  |  |
| created_at | INTEGER | NO |  |  |

### Relationships

- *(none)*

### Indexes

- **jobs_queue_index** (NON-UNIQUE) on `queue`

---

## media

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| model_type | varchar | NO |  |  |
| model_id | varchar | NO |  |  |
| uuid | varchar | YES |  |  |
| collection_name | varchar | NO |  |  |
| name | varchar | NO |  |  |
| file_name | varchar | NO |  |  |
| mime_type | varchar | YES |  |  |
| disk | varchar | NO |  |  |
| conversions_disk | varchar | YES |  |  |
| size | INTEGER | NO |  |  |
| manipulations | TEXT | NO |  |  |
| custom_properties | TEXT | NO |  |  |
| generated_conversions | TEXT | NO |  |  |
| responsive_images | TEXT | NO |  |  |
| order_column | INTEGER | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **media_order_column_index** (NON-UNIQUE) on `order_column`
- **media_uuid_unique** (UNIQUE) on `uuid`
- **media_model_type_model_id_index** (NON-UNIQUE) on `model_type, model_id`

---

## migrations

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| migration | varchar | NO |  |  |
| batch | INTEGER | NO |  |  |

### Relationships

- *(none)*

### Indexes

- *(none)*

---

## noteables

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| note_id | varchar | NO |  |  |
| noteable_type | varchar | NO |  |  |
| noteable_id | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **noteables_noteable_type_noteable_id_index** (NON-UNIQUE) on `noteable_type, noteable_id`

---

## notes

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| creator_id | varchar | YES |  |  |
| title | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| deleted_at | datetime | YES |  |  |
| creation_source | varchar | NO |  |  |

### Relationships

- notes.creator_id → users.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- notes.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_notes_1** (UNIQUE) on `id`

---

## notifications

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| type | varchar | NO |  |  |
| notifiable_type | varchar | NO |  |  |
| notifiable_id | varchar | NO |  |  |
| data | TEXT | NO |  |  |
| read_at | datetime | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **notifications_notifiable_type_notifiable_id_index** (NON-UNIQUE) on `notifiable_type, notifiable_id`
- **sqlite_autoindex_notifications_1** (UNIQUE) on `id`

---

## opportunities

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| creator_id | varchar | YES |  |  |
| company_id | varchar | YES |  |  |
| contact_id | varchar | YES |  |  |
| name | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| deleted_at | datetime | YES |  |  |
| creation_source | varchar | NO |  |  |
| order_column | numeric | YES |  |  |

### Relationships

- opportunities.contact_id → people.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- opportunities.company_id → companies.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- opportunities.creator_id → users.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- opportunities.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_opportunities_1** (UNIQUE) on `id`

---

## password_reset_tokens

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| email | varchar | NO |  | YES |
| token | varchar | NO |  |  |
| created_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **sqlite_autoindex_password_reset_tokens_1** (UNIQUE) on `email`

---

## people

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| creator_id | varchar | YES |  |  |
| company_id | varchar | YES |  |  |
| name | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| deleted_at | datetime | YES |  |  |
| creation_source | varchar | NO |  |  |

### Relationships

- people.company_id → companies.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- people.creator_id → users.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- people.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_people_1** (UNIQUE) on `id`

---

## personal_access_tokens

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| tokenable_type | varchar | NO |  |  |
| tokenable_id | varchar | NO |  |  |
| name | varchar | NO |  |  |
| token | varchar | NO |  |  |
| abilities | TEXT | YES |  |  |
| last_used_at | datetime | YES |  |  |
| expires_at | datetime | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **personal_access_tokens_token_unique** (UNIQUE) on `token`
- **personal_access_tokens_tokenable_type_tokenable_id_index** (NON-UNIQUE) on `tokenable_type, tokenable_id`

---

## sessions

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| user_id | varchar | YES |  |  |
| ip_address | varchar | YES |  |  |
| user_agent | TEXT | YES |  |  |
| payload | TEXT | NO |  |  |
| last_activity | INTEGER | NO |  |  |

### Relationships

- *(none)*

### Indexes

- **sessions_last_activity_index** (NON-UNIQUE) on `last_activity`
- **sessions_user_id_index** (NON-UNIQUE) on `user_id`
- **sqlite_autoindex_sessions_1** (UNIQUE) on `id`

---

## system_administrators

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| name | varchar | NO |  |  |
| email | varchar | NO |  |  |
| email_verified_at | datetime | YES |  |  |
| password | varchar | NO |  |  |
| role | varchar | NO |  |  |
| remember_token | varchar | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **system_administrators_email_unique** (UNIQUE) on `email`
- **system_administrators_email_index** (NON-UNIQUE) on `email`
- **sqlite_autoindex_system_administrators_1** (UNIQUE) on `id`

---

## task_user

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| task_id | varchar | NO |  |  |
| user_id | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- task_user.user_id → users.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*
- task_user.task_id → tasks.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- *(none)*

---

## taskables

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| task_id | varchar | NO |  |  |
| taskable_type | varchar | NO |  |  |
| taskable_id | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **taskables_taskable_type_taskable_id_index** (NON-UNIQUE) on `taskable_type, taskable_id`

---

## tasks

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| creator_id | varchar | YES |  |  |
| title | varchar | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| deleted_at | datetime | YES |  |  |
| creation_source | varchar | NO |  |  |
| order_column | numeric | YES |  |  |

### Relationships

- tasks.creator_id → users.id *(ON UPDATE NO ACTION, ON DELETE SET NULL)*
- tasks.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **sqlite_autoindex_tasks_1** (UNIQUE) on `id`

---

## team_invitations

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| team_id | varchar | NO |  |  |
| email | varchar | NO |  |  |
| role | varchar | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- team_invitations.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **team_invitations_team_id_email_unique** (UNIQUE) on `team_id, email`
- **sqlite_autoindex_team_invitations_1** (UNIQUE) on `id`

---

## team_user

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | INTEGER | NO |  | YES |
| team_id | varchar | NO |  |  |
| user_id | varchar | NO |  |  |
| role | varchar | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- team_user.user_id → users.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*
- team_user.team_id → teams.id *(ON UPDATE NO ACTION, ON DELETE CASCADE)*

### Indexes

- **team_user_team_id_user_id_unique** (UNIQUE) on `team_id, user_id`

---

## teams

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| user_id | varchar | NO |  |  |
| name | varchar | NO |  |  |
| personal_team | tinyint(1) | NO |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| slug | varchar | NO |  |  |

### Relationships

- *(none)*

### Indexes

- **teams_slug_unique** (UNIQUE) on `slug`
- **teams_user_id_index** (NON-UNIQUE) on `user_id`
- **sqlite_autoindex_teams_1** (UNIQUE) on `id`

---

## user_social_accounts

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| user_id | varchar | NO |  |  |
| provider_name | varchar | YES |  |  |
| provider_id | varchar | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |

### Relationships

- user_social_accounts.user_id → users.id *(ON UPDATE CASCADE, ON DELETE CASCADE)*

### Indexes

- **user_social_accounts_provider_name_provider_id_unique** (UNIQUE) on `provider_name, provider_id`
- **sqlite_autoindex_user_social_accounts_1** (UNIQUE) on `id`

---

## users

### Columns

| Column | Type | Nullable | Default | PK |
|--------|------|----------|---------|----|
| id | varchar | NO |  | YES |
| name | varchar | NO |  |  |
| email | varchar | NO |  |  |
| email_verified_at | datetime | YES |  |  |
| password | varchar | YES |  |  |
| remember_token | varchar | YES |  |  |
| current_team_id | varchar | YES |  |  |
| profile_photo_path | varchar | YES |  |  |
| created_at | datetime | YES |  |  |
| updated_at | datetime | YES |  |  |
| two_factor_secret | TEXT | YES |  |  |
| two_factor_recovery_codes | TEXT | YES |  |  |
| two_factor_confirmed_at | datetime | YES |  |  |

### Relationships

- *(none)*

### Indexes

- **users_email_unique** (UNIQUE) on `email`
- **sqlite_autoindex_users_1** (UNIQUE) on `id`

---

