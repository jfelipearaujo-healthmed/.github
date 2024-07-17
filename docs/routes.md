# Routes

### Authentication

| Method | Endpoint       | Description   | Service         |
| ------ | -------------- | ------------- | --------------- |
| POST   | /auth/login    | Login user    | Lambda Login    |
| POST   | /auth/register | Register user | Lambda Register |

### Authorizer for the API Gateway

- Lambda Authorizer will be used to validate JWT token

### User Service

| Method | Endpoint                     | User Type      | Description             | Observation                                              |
| ------ | ---------------------------- | -------------- | ----------------------- | -------------------------------------------------------- |
| GET    | /users/me                    | Doctor/Patient | Get user information    | It will return the user information                      |
| GET    | /users/me/reviews            | Doctor/Patient | Get reviews             | It will return all sent/received reviews                 |
| GET    | /users/me/reviews/{reviewId} | Doctor/Patient | Get review              | It will return the review with the given id              |
| PUT    | /users/me                    | Doctor/Patient | Update user information | It will update the user information                      |
| DELETE | /users/me                    | Doctor/Patient | Delete user information | Some information can't be deleted and will be anonymized |

### Schedule Service

| Method | Endpoint                | User Type | Description     | Observation                                            |
| ------ | ----------------------- | --------- | --------------- | ------------------------------------------------------ |
| GET    | /schedules              | Doctor    | Get schedules   | It will return all schedules                           |
| GET    | /schedules/{scheduleId} | Doctor    | Get schedule    | It will return the schedule with the given id          |
| POST   | /schedules              | Doctor    | Create schedule | Must inform a date and times, like "2021-01-01 10:00"  |
| PUT    | /schedules/{scheduleId} | Doctor    | Update schedule | If already exists appointments, it will not be updated |
| DELETE | /schedules/{scheduleId} | Doctor    | Delete schedule | If already exists appointments, it will not be deleted |

### Appointment Service

| Method | Endpoint                                                 | User Type      | Description                                | Observation                                         |
| ------ | -------------------------------------------------------- | -------------- | ------------------------------------------ | --------------------------------------------------- |
| GET    | /appointments/doctors                                    | Patient        | Get doctors by Medical ID, specialty, etc  | It will return all doctors                          |
| GET    | /appointments/doctors/{doctorId}                         | Patient        | Get doctor by ID                           | It will return the doctor with the given id         |
| GET    | /appointments                                            | Doctor/Patient | Get appointments                           | It will return all appointments                     |
| GET    | /appointments/{appointmentId}                            | Doctor/Patient | Get appointment                            | It will return the appointment with the given id    |
| PUT    | /appointments/{appointmentId}/confirmation               | Doctor         | Accept or reject the appointment           | Must inform a reason in case of rejection           |
| POST   | /appointments                                            | Patient        | Create appointment                         | Must inform the scheduleId and the doctorId         |
| PUT    | /appointments/{appointmentId}                            | Patient        | Can reschedule the appointment             |                                                     |
| POST   | /appointments/{appointmentId}/cancel                     | Doctor/Patient | Cancel the appointment                     | Must inform a reason                                |
| GET    | /appointments/{appointmentId}/feedback                   | Doctor         | Get feedbacks of the appointment           | It will return all feedbacks                        |
| POST   | /appointments/{appointmentId}/feedback                   | Patient        | Give feedback to the appointment           | Must inform a feedback and a rating between 1 and 5 |
| GET    | /appointments/{appointmentId}/feedback/{feedbackId}      | Doctor         | Get feedback of the appointment            | It will return the feedback with the given id       |
| POST   | /appointments/{appointmentId}/files                      | Patient        | Upload files to the appointment            | The files must be in PFD format                     |
| GET    | /appointments/{appointmentId}/files                      | Doctor/Patient | Get files of the appointment               | It will return all files                            |
| DELETE | /appointments/{appointmentId}/files/{file}               | Patient        | Delete file of the appointment             | It will delete the file                             |
| GET    | /appointments/{appointmentId}/files/{file}               | Doctor/Patient | Get file of the appointment                | It will return the file                             |
| GET    | /appointments/{appointmentId}/files/{file}/access        | Patient        | Get the list of who can access the file    | It will return the list of doctors                  |
| PUT    | /appointments/{appointmentId}/files/{file}/access        | Patient        | Update the list of who can access the file | It will update the list of doctors                  |
| GET    | /appointments/{appointmentId}/medical-reports            | Doctor         | Get medical reports of the appointment     | It will return all medical reports                  |
| GET    | /appointments/{appointmentId}/medical-reports/{reportId} | Doctor         | Get medical report of the appointment      | It will return the medical report with the given id |
| PUT    | /appointments/{appointmentId}/medical-reports/{reportId} | Doctor         | Update medical report of the appointment   | It will update the medical report with the given id |
