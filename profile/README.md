<p align="center">
  <img align="center" 
    src="../docs/logo.png"
    alt="Health&Med Org Logo"
    style="width: 25%;" />
</p>

# Health&Med Org

This is a project that will help the patients and doctors to manage their appointments and medical reports.

## Architecture

The following diagram shows the architecture of the project. It is was created with the following requirements in mind:

- High availability: The system should be available 24/7.
- Scalability: The system should be able to scale horizontally to handle a huge number of users (20k of patiantes at the same time).
- Security: The system should be secure to guarantee the confidentiality and integrity of the data.

![architecture](../docs/architecture.png)

## Technologies

To create this project, we used the major technologies:

- [AWS](https://aws.amazon.com/)
- [Kubernetes](https://kubernetes.io/)
- [Terraform](https://www.terraform.io/)
- [Docker](https://www.docker.com/)
- [GoLang](https://golang.org/)

## Infrastructure as Code

This project has the following services:

### [EKS Cluster IaC](https://github.com/jfelipearaujo-healthmed/eks-cluster-iac)

In this service, we provisioning the EKS cluster and other resources using Terraform.

### [Database IaC](https://github.com/jfelipearaujo-healthmed/database-iac)

In this service, we provisioning the database and other resources using Terraform.

The databases are:

- UserDB
- ScheduleDB
- AppointmentDB

Also, we use a Redis cache to avoid the overload of the database.

To see the tables, please check [this](../docs/database.md) page.

### [Queues & Topics IaC](https://github.com/jfelipearaujo-healthmed/queues-topics-iac)

To allow a huge number of users to access the API Gateway, we use the Queues and Topics from AWS to handle the creation of appointments and be able to calculate correctly the rating of each doctor.

### [API Gateway IaC](https://github.com/jfelipearaujo-healthmed/api-gateway-iac)

To allow the project be able to escale horizontally, we use the API Gateway and a NLB to handle the traffic to an Ingress Controller running on the EKS cluster.

## Microservices

### [User Service](https://github.com/jfelipearaujo-healthmed/user-service)

This service is responsible for the user management, it will create, update, get and delete users.

Also, it allow patients to search for doctors by specialty, city, state, etc.

### [Schedule Service](https://github.com/jfelipearaujo-healthmed/scheduler-service)

This service is responsible for the schedule management, it will create, update, get and delete schedules and will be used entirely by the doctors.

### [Appointment Service](https://github.com/jfelipearaujo-healthmed/appointment-service)

This is the main service of the project, it will create, update, get and delete appointments.

It will also allow the following actions:
- Confirm or decline an appointment
- Cancel an appointment
- Add feedback to an appointment
- Get feedbacks
- Upload files to an appointment
- Create a file access
- Get all files attached to an appointment
- Create a medical report
- Get all medical reports
- Get a medical report by id

### [Appointment Creator Service](https://github.com/jfelipearaujo-healthmed/appointment-creator-service)

- [ ] TODO: Desenhar os fluxos

This service is responsible to handle the creation of appointments and avoid clashes between the possible huge number of users trying to create appointments at the same time for the same doctor. To perform this task, we use a FIFO Topic and a FIFO Queue to centralize the creation of appointments and allow the correct order of the appointments.

### [Review Processor Service](https://github.com/jfelipearaujo-healthmed/review-processor-service)

- [ ] TODO: Desenhar os fluxos

This service is responsible for the process each review made by each patient and calculate the rating of each doctor. To allow a better way to calculate the rating, we use the Topic and a Queue to centralize the feedbacks and segregate the processing power needed to calculate the rating away from the appointment service.

## Routes

If you want to have a better understanding of the routes, please check [this](../docs/routes.md) page.
