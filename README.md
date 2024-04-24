# Cloud Native Web Application for CI-CD pipeline.

## Overview

This GitHub Actions workflow(packerBuild.yml) automates the building and deployment process of a Packer image for a Maven-based Java web application on Google Cloud Platform (GCP). Upon merging pull requests into the `main` branch, the workflow triggers a series of steps to ensure a seamless deployment pipeline.

### 1. Workflow Initialization and Dependency Installation:

The workflow initiates upon the merging of pull requests into the `main` branch, triggering an automated deployment pipeline. Initially, essential dependencies including Maven, PostgreSQL, and Packer are installed on the designated Ubuntu environment. Additionally, environment variables containing sensitive information such as database credentials and GCP metadata are configured, laying the foundation for secure and efficient deployment.

### 2. Application Testing and Packer Configuration:

With the environment set up, the workflow proceeds to execute integration and unit tests using Maven, validating the integrity and functionality of the Java web application. Following successful testing, Packer configuration files are initialized, formatted, and validated to ensure consistency and adherence to best practices. These meticulous preparations pave the way for the subsequent building and deployment stages.

### 3. Packer Image Building and GCP Deployment:

The workflow enters the core phase of image building and deployment on Google Cloud Platform. Leveraging Packer, the Java application is encapsulated into a custom image, tailored to the specified requirements and configurations. The built image is then seamlessly deployed to GCP, where it forms the foundation for scalable and resilient application instances.

### 4. Continuous Monitoring and Finalization:

As the deployment progresses, the workflow continuously monitors the status of the GCP instance group manager, ensuring that the version target is reached. This meticulous monitoring ensures that the deployment is completed successfully, minimizing downtime and disruptions. Upon reaching the version target, the deployment pipeline concludes, marking a successful iteration of the build and deployment process.

## Repository Setup

Ensure the necessary directory structure and configuration files are present in your repository:

- `packer/`: Directory containing Packer configuration files.
- `systemd/`: Directory containing systemd configuration files for the application.
- `target/web-app-0.0.1-SNAPSHOT.jar`: Built JAR file of the Maven project.
- `opsagent/config.yaml`: Configuration file for operational agents.
- `.env`: Environment file containing database credentials.

## Usage

1. Configure necessary secrets in organization GitHub repository settings, including database credentials from terraform infra, GCP credentials, and other environment variables referenced in the workflow.
2. Merge pull requests into the `main` branch to trigger the workflow.
3. Monitor the workflow execution and check the GCP Console for deployment status.

## Getting Started

### Prerequisites

- [Java](https://www.java.com/) installed on your machine
- [Maven](https://maven.apache.org/) installed on your machine

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/cloudapp6225/webapp.git

2. Install postgresql server

    ```bash
    sudo apt install -y postgresql postgresql-contrib

3. Navigate to the project

   ```bash
   cd webapp/

4. Build project

    ```bash
    mvn clean install

5.  Run Locally

    ```bash
    mvn spring-boot:run

## Development

### User Schema

```
{
    id:	string($uuid)
    first_name: string
    last_name: string
    password: string($password)
    username: string($email)
    account_created: string($date-time)
    account_updated: string($date-time)
}
```
### Testing

- [Postman client](https://www.postman.com/) install on your machine

### API Endpoints

### `POST http://localhost:8080/v1/user`
Create a new User
```
{
  "first_name": "Jane",
  "last_name": "Doe",
  "password": "skdjfhskdfjhg",
  "username": "jane.doe@example.com"
}
```
### Authenticated Endpoints
### `GET http://localhost:8080/v1/user/self`
Get a user by passing username and password in basic authentication header.

### `PUT http://localhost:8080/v1/user/self`
Update user details by providing authentication headers.

## Packer Commands


```bash
$ packer init ./packer/.
$ packer fmt ./packer/.
$ packer validate -var 'project_id=dev-gcp-project-1' -var 'source_jar=./target/web-app-0.0.1-SNAPSHOT.jar' -var 'source_env=./.env' -var 'source_systemd=./systemd/webapp.service' ./packer/.
$ packer build -var 'project_id=dev-gcp-project-1' -var 'source_jar=./target/web-app-0.0.1-SNAPSHOT.jar' -var 'source_env=./.env' -var 'source_systemd=./systemd/webapp.service' ./packer/.

