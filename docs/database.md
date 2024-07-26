# 📖 Bancos de Dados

### 📚 UserDB

#### 📋 Table `users`

| Nome da Coluna | Tipo   | Descrição                                 |
| -------------- | ------ | ----------------------------------------- |
| id             | uint   | Chave Primária                            |
| email          | string | E-mail                                    |
| password       | string | Senha                                     |
| full_name      | string | Nome Completo                             |
| document_id    | string | CPF                                       |
| phone          | string | Telefone                                  |
| role           | string | Papel no sistema (admin, doctor, patient) |

#### 📋 Table `doctors`

| Nome da Coluna | Tipo   | Descrição          |
| -------------- | ------ | ------------------ |
| id             | uint   | Chave Primária     |
| user_id        | uint   | ID do Usuário      |
| specialty      | string | Especialidade      |
| medical_id     | string | CRM                |
| price          | number | Preço              |
| avg_rating     | number | Avaliação Media    |
| total_patients | int    | Total de Pacientes |

#### 📋 Table `addresses`

| Nome da Coluna | Tipo   | Descrição      |
| -------------- | ------ | -------------- |
| id             | uint   | Chave Primária |
| user_id        | uint   | ID do Usuário  |
| street         | string | Rua            |
| number         | string | Numero         |
| neighborhood   | string | Bairro         |
| city           | string | Cidade         |
| state          | string | Estado         |
| zip_code       | string | CEP            |

### 📚 ScheduleDB

#### 📋 Table `schedules`

| Nome da Coluna      | Tipo     | Descrição              |
| ------------------- | -------- | ---------------------- |
| id                  | uint     | Chave Primária         |
| doctor_id           | uint     | ID do Medico           |
| date_time_available | datetime | Data e hora disponível |
| active              | boolean  | Ativo                  |

### 📚 AppointmentDB

#### 📋 Table `appointments`

| Nome da Coluna      | Tipo     | Descrição                          |
| ------------------- | -------- | ---------------------------------- |
| id                  | uint     | Chave Primária                     |
| schedule_id         | uint     | ID da Agenda                       |
| doctor_id           | uint     | ID do Medico                       |
| patient_id          | uint     | ID do Paciente                     |
| date_time           | datetime | Data e hora escolhida pelo usuário |
| status              | string   | Status da Consulta                 |
| start_at            | datetime | Iniciado em                        |
| end_at              | datetime | Finalizado em                      |
| confirmed_at        | datetime | Confirmado em                      |
| cancelled_by        | uint     | Cancelado por                      |
| cancelled_at        | datetime | Cancelado em                       |
| cancellation_reason | string   | Motivo do Cancelamento             |

#### 📋 Table `events`

| Nome da Coluna | Tipo   | Descrição                |
| -------------- | ------ | ------------------------ |
| id             | uint   | Chave Primária           |
| user_id        | uint   | ID do Usuário            |
| message_id     | string | ID da Mensagem do Tópico |
| event_Tipo     | string | Tipo de Evento           |
| data           | string | Dados do Evento em JSON  |
| outcome        | string | Saída do Evento          |

#### 📋 Table `reviews`

| Nome da Coluna | Tipo   | Descrição      |
| -------------- | ------ | -------------- |
| id             | uint   | Chave Primária |
| appointment_id | uint   | ID da Consulta |
| rating         | number | Avaliação      |
| comment        | string | Comentário     |

#### 📋 Table `files`

| Nome da Coluna     | Tipo   | Descrição                |
| ------------------ | ------ | ------------------------ |
| id                 | uint   | Chave Primária           |
| patient_id         | uint   | ID do Paciente           |
| file_name          | string | Nome do Arquivo          |
| file_original_name | string | Nome Original do Arquivo |
| file_extension     | string | Extensão do Arquivo      |
| file_size          | number | Tamanho do Arquivo       |
| file_url           | string | URL do Arquivo           |

#### 📋 Table `file_access`

| Nome da Coluna | Tipo     | Descrição                   |
| -------------- | -------- | --------------------------- |
| id             | uint     | Chave Primária              |
| user_id        | uint     | ID do Usuário               |
| file_id        | uint     | ID do Arquivo               |
| doctor_id      | uint     | ID do Medico                |
| appointment_id | uint     | ID da Consulta              |
| expires_at     | datetime | Data de Expiração do Acesso |

#### 📋 Table `medical_reports`

| Nome da Coluna | Tipo   | Descrição      |
| -------------- | ------ | -------------- |
| id             | uint   | Chave Primária |
| appointment_id | uint   | ID da Consulta |
| report         | string | Prontuario     |
