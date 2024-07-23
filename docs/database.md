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

#### Table `addresses`

| Column Name  | Type   | Description  |
| ------------ | ------ | ------------ |
| id           | uint   | Primary Key  |
| user_id      | uint   | User ID      |
| street       | string | Street       |
| number       | string | Number       |
| neighborhood | string | Neighborhood |
| city         | string | City         |
| state        | string | State        |
| zip_code     | string | Zip Code     |

### ScheduleDB

#### Table `schedules`

| Column Name         | Type     | Description                  |
| ------------------- | -------- | ---------------------------- |
| id                  | uint     | Primary Key                  |
| doctor_id           | uint     | Doctor ID                    |
| date_time_available | datetime | Date with the available time |
| active              | boolean  | Active                       |

### AppointmentDB

#### Table `appointments`

| Column Name         | Type     | Description                  |
| ------------------- | -------- | ---------------------------- |
| id                  | uint     | Primary Key                  |
| schedule_id         | uint     | Schedule ID                  |
| doctor_id           | uint     | Doctor ID                    |
| patient_id          | uint     | Patient ID                   |
| date_time           | datetime | Date date chosen by the user |
| status              | string   | Appointment Status           |
| start_at            | datetime | Start At                     |
| end_at              | datetime | End At                       |
| confirmed_at        | datetime | Confirmed At                 |
| cancelled_by        | uint     | Cancelled By                 |
| cancelled_at        | datetime | Cancelled At                 |
| cancellation_reason | string   | Cancellation Reason          |

#### Table `events`

| Column Name | Type   | Description                   |
| ----------- | ------ | ----------------------------- |
| id          | uint   | Primary Key                   |
| user_id     | uint   | User ID                       |
| message_id  | string | Message ID from Topic service |
| event_type  | string | Event Type                    |
| data        | string | Event Data in JSON            |
| outcome     | string | Event Outcome                 |

#### Table `reviews`

| Column Name    | Type   | Description    |
| -------------- | ------ | -------------- |
| id             | uint   | Primary Key    |
| appointment_id | uint   | Appointment ID |
| rating         | number | Rating         |
| comment        | string | Comment        |

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
