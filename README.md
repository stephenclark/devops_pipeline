# devops_pipeline

Example of a medium complexity CiCd pipeline using Jenkins, Docker, Ansible, K8s, with monitoring.

## Jenkins & Jfrog Artifactory

For this project Jenkins adn Jfrog are set up using Docker-Compose

```bash
# Launch Jenkins & Jfrog in docker containers
docker-compose -f docker-compose-CI-CD.yml up -d
```
## Jenkins, initial setup

```bash
# Retrieve the Jenkins admin Password
docker exec devops_pipeline_jenkins_1 cat /var/jenkins_home/secrets/initialAdminPassword

```
http://localhost:8080 to access jenkins UI


For this project I selected No plugins, as I will install them later as I need them to keep the docker image small.

Create a Jenkins User:
username : admin
password : password  


### Installing Jenkins Plugins

- Git Plugin: git_plugin
- Workspace Cleanup Plugin: ws-ws_cleanup_plugin
- Maven Plugin: maven_plugin
- NodeJS Plugin: nodejs_plugin
- Go Plugin: go_plugin
- Git Tag Plugin: git_tag_plugin
- Ssh Plugin: ssh_plugin
- Artifactory Plugin: artifactory_plugin


## Artifactory
http://localhost:8081 to access artifactory UI
Default Credentials:
username : admin
password : password  
After login in you will be welcomed with this page.

welcome

Skip password change and proxy creation.

Select Maven

create

Then click on finish.


Using Jenkins

A test job and a user with access token have been set up in the interface and the job can be launched with:
http://admin:115a2eb5599581ca8ebabb5a088500b295@localhost:8080/job/job1/build?token=randomtoken