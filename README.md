# BoardgameListingWebApp

## Description

**Board Game Database Full-Stack Web Application.**
This web application displays lists of board games and their reviews. While anyone can view the board game lists and reviews, they are required to log in to add/ edit the board games and their reviews. The 'users' have the authority to add board games to the list and add reviews, and the 'managers' have the authority to edit/ delete the reviews on top of the authorities of users.  

## Technologies

- Java
- Spring Boot
- Amazon Web Services(AWS) EC2
- Thymeleaf
- Thymeleaf Fragments
- HTML5
- CSS
- JavaScript
- Spring MVC
- JDBC
- H2 Database Engine (In-memory)
- JUnit test framework
- Spring Security
- Twitter Bootstrap
- Maven

## Features

- Full-Stack Application
- UI components created with Thymeleaf and styled with Twitter Bootstrap
- Authentication and authorization using Spring Security
  - Authentication by allowing the users to authenticate with a username and password
  - Authorization by granting different permissions based on the roles (non-members, users, and managers)
- Different roles (non-members, users, and managers) with varying levels of permissions
  - Non-members only can see the boardgame lists and reviews
  - Users can add board games and write reviews
  - Managers can edit and delete the reviews
- Deployed the application on AWS EC2
- JUnit test framework for unit testing
- Spring MVC best practices to segregate views, controllers, and database packages
- JDBC for database connectivity and interaction
- CRUD (Create, Read, Update, Delete) operations for managing data in the database
- Schema.sql file to customize the schema and input initial data
- Thymeleaf Fragments to reduce redundancy of repeating HTML elements (head, footer, navigation)

## How to Run

1. Clone the repository
2. Open the project in your IDE of choice
3. Run the application
4. To use initial user data, use the following credentials.
  - username: bugs    |     password: bunny (user role)
  - username: daffy   |     password: duck  (manager role)
5. You can also sign-up as a new user and customize your role to play with the application! 😊

1 Master and 2 Worker Nodes - t2.med
folow steps from k8s-setup
master: kubectl get nodes (1-master, 2-worker)

sonarqube and nexus - t2.med
sudo apt update
install docker
sudo chmod 666 /var/run/docker.sock

sonarqube:
docker run -d -p 9000:9000 sonarqube:lts-community
chrome: publicIP:9000 (admin/admin, later get token)

nexus:
docker run -d -p 8081:8081 sonatype/nexus3:latest
chrome: publicIP:8081 (admin/get pwd from ..)
docker exec -it containerID /bin/bash
cat sonatype-work/nexus3/admin-password (copy password)

jenkins - t2.large
sudo apt update
install jdk17
install jenkins
install docker
chrome: publicIP:8080
install Trivy

Jenkins dashboard:

manage jenkins/plugins/available plugins

Eclipse Temurin installer (jdk)
Config File Provider (maven)
Pipeline Maven Integration (maven)
Maven Integration
SonarQube Scanner
docker
docker pipeline
kubernetes
Kubernetes Client API
kubernetes cli
Kubernetes Credentials

manage jenkins/Tools

jdk
sonarqube
maven
docker

New item/create: BoardGame/Pipeline

creating pipeline










