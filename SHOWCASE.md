# ping-jui.com: a markdown service
You can sign up an account, use Markdownb file to present you project to people


## Software Stack
I value **Portability**, **Scalabitliy**, and **Reliabiltiy**, because I do not know how the project will grow in the future.  
**Docker** and **docker-compose** have made my life so much easier.
Currently, the software stack looks like this.
![Software Stack](https://github.com/pingjuiliao/ping-jui.com_public/blob/main/img/software_stack.png?raw=true)

This is a **Docker-In-Docker** model, in which **Jenkins** are allowed to request a docker service for CI/CD pipeline.  
Only for those tools that has beautiful output and configuration, I choose to run them in a seperated Docker Container.  


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


## Developer Note
My goal for this hosted websites is to gain experiences with modern techniques in Cloud Backend Development.
I put notes like **what the challenges are** and **what could have been more effective**.

### AWS Instance setup and management
1. After launching the instance, it is NOT as simple as mapping the DNS to the public IP addresses. We need to define **Security Group** and define HTTP/HTTPS policies.
2. SSH to the EC2 instance: after getting into the instance on your browser root, better to create another account for launching services.
```
# Do not use 'adduser' because 'useradd' setup many things for us.
useradd -m new_user
```
3. Do not use the terminal in browser: issue like this is that `vim` cannot escape via `:` command.

I plan to try more AWS features in the future. Hopefully, docker can make the deployment much easier

### Deploying with HTTPS
Deploying with [TLS/SSL](https://en.wikipedia.org/wiki/Transport_Layer_Security) was challenging to me. I have read OpenSSL's document and learn what X509 certificates is and purchases with [Certificate Authority (CA)](https://en.wikipedia.org/wiki/Certificate_authority). This requires you to sign with your private key. OpenSSL has made things easier.  
An issue with this is that developers often tests software with HTTP instead of HTTPS protocols. The time I made it to deploy on **https://www.ping-jui.com**, I loses the ability to connect on **http://localhost**. This prevents me to do some testing before deployment. At first, there are some ways to bypass it.

### Jenkins Configuration as Code
Jenkins provides awesome pipeline yet requires lots of manual configurations.  
At first, I have to setup a list of plugins, credentials, and system connection and tools manually.
Not until I googled Jenkisn Configuration as Code did I know that configuration is possible.  
Now, I have installed all the plugins via **jenkins CLI**.
For credentials and other configuration, it's very trivial to configure as the code.

## Comming Soon (TODO list for myself)
+ Ratings & Tags features on Projects
+ UI Testing via Selenium
+ Redis (NoSQL and memory cache)
+ Kubernetes
