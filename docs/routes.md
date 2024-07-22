# Routes

### Authentication

| Method | Endpoint       | Description   | Service         |
| ------ | -------------- | ------------- | --------------- |
| POST   | `/auth/login`    | Login user    | Lambda Login    |
| POST   | `/auth/register` | Register user | Lambda Register |

### Authorizer for the API Gateway

- Lambda Authorizer will be used to validate JWT token

### User Service

| Method | Endpoint                    | Description                               | User Role      |
| ------ | --------------------------- | ----------------------------------------- | -------------- |
| POST   | `/users`                    | Create a user                             | Doctor/Patient |
| GET    | `/users/me`                 | Get the current user                      | Doctor/Patient |
| PUT    | `/users/me`                 | Update a user                             | Doctor/Patient |
| GET    | `/users/doctors`            | Get doctors by Medical ID, specialty, etc | Patient        |
| GET    | `/users/doctors/{doctorId}` | Get doctor by ID                          | Patient        |

### Scheduler Service

| Method | Endpoint                  | Description                     | User Role |
| ------ | ------------------------- | ------------------------------- | --------- |
| GET    | `/schedules`              | It will return all schedules    | Doctor    |
| GET    | `/schedules/{scheduleId}` | It will return a schedule by id | Doctor    |
| POST   | `/schedules`              | It will create a schedule       | Doctor    |
| PUT    | `/schedules/{scheduleId}` | It will update a schedule       | Doctor    |
| DELETE | `/schedules/{scheduleId}` | It will delete a schedule       | Doctor    |

### Appointment Service

| Method | Endpoint                                               | Description                              | User Role      |
| ------ | ------------------------------------------------------ | ---------------------------------------- | -------------- |
| POST   | `/appointments`                                        | Create an appointment via event          | Patient        |
| GET    | `/appointments`                                        | Get all appointments                     | Doctor/Patient |
| GET    | `/appointments/{appointmentId}`                        | Get an appointment by id                 | Doctor/Patient |
| PUT    | `/appointments/{appointmentId}`                        | Update an appointment                    | Patient        |
| POST   | `/appointments/{appointmentId}/confirmation`           | Confirm or decline an appointment        | Doctor         |
| POST   | `/appointments/{appointmentId}/cancel`                 | Reschedule an appointment                | Doctor/Patient |
| POST   | `/appointments/{appointmentId}/feedbacks`              | Add feedback to an appointment via event | Patient        |
| GET    | `/appointments/{appointmentId}/feedbacks`              | Get feedbacks                            | Doctor/Patient |
| GET    | `/appointments/{appointmentId}/feedbacks/{feedbackId}` | Get feedback by id                       | Doctor/Patient |
| POST   | `/files`                                               | Update files                             | Patient        |
| GET    | `/files`                                               | Get all files                            | Patient        |
| GET    | `/files/{fileId}`                                      | Get a file by id                         | Doctor/Patient |
| POST   | `/files/{fileId}/access`                               | Create a file access                     | Patient        |
| GET    | `/files/{fileId}/access`                               | Get all file access                      | Patient        |
| GET    | `/files/{fileId}/access/{accessId}`                    | Get a file access by id                  | Patient        |
| PUT    | `/files/{fileId}/access/{accessId}`                    | Update a file access                     | Patient        |
| DELETE | `/files/{fileId}/access/{accessId}`                    | Delete a file access                     | Patient        |
| POST   | `/medical-reports`                                     | Create a medical report                  | Doctor         |
| GET    | `/medical-reports`                                     | Get all medical reports                  | Doctor         |
| GET    | `/medical-reports/{medicalReportId}`                   | Get a medical report by id               | Doctor         |
| PUT    | `/medical-reports/{medicalReportId}`                   | Update a medical report                  | Doctor         |
| DELETE | `/medical-reports/{medicalReportId}`                   | Delete a medical report                  | Doctor         |

