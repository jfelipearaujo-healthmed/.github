# Database

### UserDB

#### Table `users`

| Column Name | Type   | Description                   |
| ----------- | ------ | ----------------------------- |
| id          | uint   | Primary Key                   |
| email       | string | Email                         |
| password    | string | Password                      |
| full_name   | string | Full Name                     |
| document_id | string | Document ID (CPF)             |
| phone       | string | Phone Number                  |
| role        | string | Role (admin, doctor, patient) |

#### Table `doctors`

| Column Name    | Type   | Description           |
| -------------- | ------ | --------------------- |
| id             | uint   | Primary Key - User ID |
| user_id        | uint   | User ID               |
| specialty      | string | Specialty             |
| medical_id     | string | Medical ID (CRM)      |
| price          | number | Price                 |
| avg_rating     | number | Average Rating        |
| total_patients | int    | Total Patients        |

### ScheduleDB

#### Table `schedules`

| Column Name | Type    | Description |
| ----------- | ------- | ----------- |
| id          | uint    | Primary Key |
| doctor_id   | uint    | Doctor ID   |
| date        | string  | Date        |
| time        | string  | Time        |
| active      | boolean | Active      |

### AppointmentDB

#### Table `appointments`

| Column Name         | Type     | Description         |
| ------------------- | -------- | ------------------- |
| id                  | uint     | Primary Key         |
| schedule_id         | uint     | Schedule ID         |
| doctor_id           | uint     | Doctor ID           |
| patient_id          | uint     | Patient ID          |
| date                | string   | Date                |
| spot                | string   | Time                |
| start_at            | datetime | Start At            |
| end_at              | datetime | End At              |
| confirmed_at        | datetime | Confirmed At        |
| cancelled_by        | uint     | Cancelled By        |
| cancelled_at        | datetime | Cancelled At        |
| cancellation_reason | string   | Cancellation Reason |

#### Table `reviews`

| Column Name    | Type   | Description    |
| -------------- | ------ | -------------- |
| id             | uint   | Primary Key    |
| appointment_id | uint   | Appointment ID |
| rating         | number | Rating         |
| feedback       | string | Feedback       |

#### Table `files`

| Column Name        | Type   | Description        |
| ------------------ | ------ | ------------------ |
| id                 | uint   | Primary Key        |
| patient_id         | uint   | Patient ID         |
| file_id            | uuid   | File ID            |
| file_original_name | string | File Original Name |
| file_type          | string | File Type          |
| file_size          | number | File Size          |
| file_url           | string | File URL           |

#### Table `file_access`

| Column Name     | Type     | Description     |
| --------------- | -------- | --------------- |
| id              | uint     | Primary Key     |
| appointment_id  | uint     | Appointment ID  |
| file_id         | uint     | File ID         |
| doctor_id       | uint     | Doctor ID       |
| expiration_date | datetime | Expiration Date |

#### Table `medical_reports`

| Column Name    | Type   | Description    |
| -------------- | ------ | -------------- |
| id             | uint   | Primary Key    |
| appointment_id | uint   | Appointment ID |
| report         | string | Report         |
