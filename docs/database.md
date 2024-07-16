# Database

### UserDB

#### Table `users`

| Column Name | Type   | Description                   |
| ----------- | ------ | ----------------------------- |
| id          | uuid   | Primary Key                   |
| email       | string | Email                         |
| password    | string | Password                      |
| full_name   | string | Full Name                     |
| document_id | string | Document ID (CPF)             |
| phone       | string | Phone Number                  |
| role        | string | Role (admin, doctor, patient) |

#### Table `doctors`

| Column Name | Type   | Description           |
| ----------- | ------ | --------------------- |
| id          | uuid   | Primary Key - User ID |
| specialty   | string | Specialty             |
| medical_id  | string | Medical ID            |
| price       | number | Price                 |
| avg_rating  | number | Average Rating        |

### ScheduleDB

#### Table `schedules`

| Column Name | Type    | Description |
| ----------- | ------- | ----------- |
| id          | uuid    | Primary Key |
| doctor_id   | uuid    | Doctor ID   |
| date        | string  | Date        |
| spots       | string  | Times       |
| active      | boolean | Active      |

### AppointmentDB

#### Table `appointments`

| Column Name         | Type     | Description         |
| ------------------- | -------- | ------------------- |
| id                  | uuid     | Primary Key         |
| schedule_id         | uuid     | Schedule ID         |
| doctor_id           | uuid     | Doctor ID           |
| patient_id          | uuid     | Patient ID          |
| date                | string   | Date                |
| spot                | string   | Time                |
| start_at            | datetime | Start At            |
| end_at              | datetime | End At              |
| confirmed_at        | datetime | Confirmed At        |
| cancelled_by        | uuid     | Cancelled By        |
| cancelled_at        | datetime | Cancelled At        |
| cancellation_reason | string   | Cancellation Reason |

#### Table `appointment_reviews`

| Column Name    | Type   | Description    |
| -------------- | ------ | -------------- |
| id             | uuid   | Primary Key    |
| appointment_id | uuid   | Appointment ID |
| doctor_id      | uuid   | Doctor ID      |
| patient_id     | uuid   | Patient ID     |
| rating         | number | Rating         |
| feedback       | string | Feedback       |

#### Table `appointment_files`

| Column Name        | Type   | Description        |
| ------------------ | ------ | ------------------ |
| id                 | uuid   | Primary Key        |
| appointment_id     | uuid   | Appointment ID     |
| file_id            | uuid   | File ID            |
| file_original_name | string | File Original Name |
| file_type          | string | File Type          |
| file_size          | number | File Size          |
| file_url           | string | File URL           |

#### Table `appointment_file_access`

| Column Name     | Type     | Description     |
| --------------- | -------- | --------------- |
| id              | uuid     | Primary Key     |
| file_id         | uuid     | File ID         |
| doctor_id       | uuid     | Doctor ID       |
| expiration_date | datetime | Expiration Date |

#### Table `medical_reports`

| Column Name    | Type   | Description    |
| -------------- | ------ | -------------- |
| id             | uuid   | Primary Key    |
| appointment_id | uuid   | Appointment ID |
| report         | string | Report         |