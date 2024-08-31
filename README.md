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
sudo su (from root only)
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
sudo chmod 666 /var/run/docker.sock
chrome: publicIP:8080
install Trivy
install kubectl

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
pipeline stage view

manage jenkins/Tools - 4

jdk
sonarqube
maven
docker

credentials: 3
github - if it is private
k8s (below)
docker
sonarqube

manage jenkins/system - 1

Sonarqube


New item/create: BoardGame/Pipeline

creating pipeline

For Quality Gate:

goto sonarqube dashboard/administration/configuration/webhooks/create
name: jenkins
URL: jenkins url/sonarqube-webhook/
create

for Publish to Nexus:
change url's in pom.xml
manage jenkins/managed files/add/global maven settings/ID: global-settings/next
change servers info


((Master:
create svc, role, bind, secret, ns (webapps) and apply
kubectl describe secret mysecretname -n webapps (copy token) and later put it in credentials))

for kubernetes server end point
cd ~/.kube
cat config
copy  https://172.31.45.20:6443

kubectl get nodes - 1 master, 2 worker
kubectl get pods -n webapps - 2
kubectl get svc -n webapps - 80:31672/TCP
chrome: masterIP:31672

Notification Email:

https://myaccount.google.com/apppasswords (goto the link/type jenkins/copy password)
manage jenkins/system/

Email notification (open port 465 for smtp gmail in ec2 security group)
SMTP server: smtp.gmail.com
advanced/Use SMTP Authentication: provide gmail pvk.raja@gmail.com
password: paste password which was created)
check use SSL
smtp port: 465
Test e-mail recipient: pvk.raja@gmail.com

Extended E-mail Notification
SMTP server: smtp.gmail.com
smtp port: 465
advanced/create credentials/username with password
user: pvk.raja@gmail.com
password: pwd which we created
mail-cred/add
check use SSL
save

buildnow

dashboard/app/build number/workspaces//var/lib/jenkins/workspace/Boardgame on built-in/fs.html and image.html

EC2: monitoring (t2.large)

sudo apt update

chrome: prometheus.io/download/prometheus for linux
wget (url link)/ls
tar -xvf <tar file> (to unzip)

chrome: prometheus.io/download/blackbox exporter for linux
wget (url link)/ls
tar -xvf <tar file> (to unzip)

chrome: graphana download - 3 steps to install

chrome: pvublicIP:3000 (for Graphana)
default: admin/admin

cd prometheus
./prometheus & (so that it runs in background)

chrome: publicIP:9090 (for prometheus)

cd ..
cd blackbox
./blackbox_exporter &

chrome: publicIP:9115 (for blackbox exporter)

cd ..
cd prometheus
vi prometheus.yml (paste)
change blackbox IP/and modify the URL's you wish to monitor (no godaddy domain)/monitor http:jenkinsIP:8080 and http://prometheus.io - 2 targets

pgrep prometheus (2216)
kill 2216
./prometheus &
goto prometheus dashboard/refresh/status/targets
2 targets are getting monitored in prometheus

goto graphana dashboard/connections/data sources/add data source/select prometheus
provide prometheus url/save and test
right corner/import dashboard
chrome: blackbox dashboard id/goto Prometheus Blackbox Exporter (graphana labs) - ID 7587
copy ID/paste/load
select datasource - prometheus/import

2 targets (http:jenkinsIP:8080 and http://prometheus.io) are getting monitored in Graphana








