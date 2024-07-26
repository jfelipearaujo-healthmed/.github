# 🌎 Rotas

### 🖥️ User Service

| Método | Rota                                | Descrição                                                | Papel do Usuário |
| ------ | ----------------------------------- | -------------------------------------------------------- | ---------------- |
| POST   | `/users/login`                      | Login de um usuário                                      | Médico/Paciente  |
| POST   | `/users`                            | Cria um usuário                                          | Médico/Paciente  |
| GET    | `/users/me`                         | Obtém o usuário atual                                    | Médico/Paciente  |
| PUT    | `/users/me`                         | Atualiza um usuário                                      | Médico/Paciente  |
| GET    | `/users/doctors`                    | Obtém médicos por ID, especialidade, cidade, estado, etc | Paciente         |
| GET    | `/users/doctors/{doctorId}`         | Obtém o médico por ID                                    | Paciente         |
| POST   | `/users/doctors/{doctorId}/ratings` | Avalia um médico                                         | Paciente         |

### 🖥️ Scheduler Service

| Método | Rota                      | Descrição               | Papel do Usuário |
| ------ | ------------------------- | ----------------------- | ---------------- |
| GET    | `/schedules`              | Obtém todas as agendas  | Médico           |
| GET    | `/schedules/{scheduleId}` | Obtém uma agenda por ID | Médico           |
| POST   | `/schedules`              | Cria uma agenda         | Médico           |
| PUT    | `/schedules/{scheduleId}` | Atualiza uma agenda     | Médico           |
| DELETE | `/schedules/{scheduleId}` | Exclui uma agenda       | Médico           |

### 🖥️ Appointment Service

| Método | Rota                                                              | Descrição                                       | Papel do Usuário |
| ------ | ----------------------------------------------------------------- | ----------------------------------------------- | ---------------- |
| POST   | `/appointments`                                                   | Cria uma consulta via evento                    | Paciente         |
| GET    | `/appointments`                                                   | Obtém todas as consultas                        | Médico/Paciente  |
| GET    | `/appointments/{appointmentId}`                                   | Obtém uma consulta por ID                       | Médico/Paciente  |
| PUT    | `/appointments/{appointmentId}`                                   | Atualiza uma consulta                           | Paciente         |
| POST   | `/appointments/{appointmentId}/confirm`                           | Confirma ou recusa uma consulta                 | Médico           |
| POST   | `/appointments/{appointmentId}/cancel`                            | Cancela uma consulta                            | Médico/Paciente  |
| POST   | `/appointments/{appointmentId}/feedbacks`                         | Adiciona feedback a uma consulta via evento     | Paciente         |
| GET    | `/appointments/{appointmentId}/feedbacks`                         | Obtém feedbacks                                 | Médico/Paciente  |
| GET    | `/appointments/{appointmentId}/feedbacks/{feedbackId}`            | Obtém feedback por ID                           | Médico/Paciente  |
| GET    | `/appointments/{appointmentId}/files`                             | Obtém todos os arquivos anexados a uma consulta | Médico           |
| POST   | `/files`                                                          | Atualiza arquivos                               | Paciente         |
| GET    | `/files`                                                          | Obtém todos os arquivos                         | Paciente         |
| GET    | `/files/{fileId}`                                                 | Obtém um arquivo por ID                         | Paciente         |
| POST   | `/files/{fileId}/access`                                          | Cria um acesso de arquivo                       | Paciente         |
| GET    | `/files/{fileId}/access`                                          | Obtém todos os acessos de arquivo               | Paciente         |
| POST   | `/appointments/{appointmentId}/medical-reports`                   | Cria um prontuário médico                       | Médico           |
| GET    | `/appointments/{appointmentId}/medical-reports`                   | Obtém todos os prontuários médicos              | Médico           |
| GET    | `/appointments/{appointmentId}/medical-reports/{medicalReportId}` | Obtém um prontuário médico por ID               | Médico           |
