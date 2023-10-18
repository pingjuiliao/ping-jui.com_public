# ping-jui.com
A markdown service that showing off your engineering projects.

## Software Stack
As the website usage scale is unknown, I value **Portability**, **Scalabitliy**, and **Reliabiltiy**.
**Docker** and **docker-compose** have made my life so much easier.
Currently, the software stack looks like this.
![Software Stack](https://github.com/pingjuiliao/ping-jui.com_public/blob/main/img/software_stack.png?raw=true)

This is a **Docker-In-Docker** model, in which **Jenkins** are allowed to request a docker service for CI/CD pipeline.  
Only for those tools that has beautiful output and configuration, I choose to run them in a seperated Docker Container.  

## 

## Jenkins pipeline (CI/CD results)
![jenkins_pipeline](https://github.com/pingjuiliao/ping-jui.com_public/blob/main/img/jenkins_pipeline.png?raw=true)
**SonarQube**: for static analysis
**OWASP Dependency Check**: for vulnerabiltiy reports
**Trivy**: for fs and image scanning

### SonarQube: static analysis
SonarQube detects vulnerablities and bugs in code in the early stages.
This is my first result:
![sonarqube_result_buggy](https://github.com/pingjuiliao/ping-jui.com_public/blob/main/img/sonarqube_result_buggy.png?raw=true)

Apparently, I have made some mistakes in developing the project. Now they are all fixed thanks to the detection.

