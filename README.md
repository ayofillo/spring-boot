# VMS Microservices

Server details - https://wiki.incomm.com/pages/viewpage.action?spaceKey=FSD&title=Microservices+Server+Details

- vms-otp : 7005
- vms-event-processing : 7006
- vms-serial-data : 7008
- vms-batch-jobs : 7009
- vms-batch-jobs-ui : 7011
- vms-flex : 7020

## Services
- vms-otp: Microservice to generate and validate OTP. [Details](/vms-otp/README.md)
- vms-event-processing: [Details](/vms-event-processing/README.md) 

## Library Modules:
- vms-notification - Module to send notifications to users via ECNS. [Details](/vms-notification/README.md)

## Deploying Micro-services
 
Each environment will have it's own configuration file which will be automatically populated based on the profile used during the deployment.
All common properties will be maintained in common "application.properties" file which will be copied to each environment.  

Will use embedded tomcat server & jar files will be picked from "apps" folder maintained in each environment.

Folder structures:

/home/InComm/vms-ms
- /config (each micro-service will have it's own folder)
    - /vms-otp
        - application.properties (common to all environments)
        - application-deva.properties
        - application-qab.properties
        - application-qaa.properties
        - application-uat.properties
    - /another-micro-service
        - property files
- /apps (startup scripts will pick jar files from here)
    - vms-otp-R.20.2.0-SNAPSHOT.jar
    - vms-[other microservice].jar
- /scripts
    - start & stop scripts
- /logs (each micro-service will have it's own log file)
    - vms-otp.log
    - vms-[microservice-name].log

Unlike in existing host application, configurations will be version controlled. 
Once we have config server integrated, we can simply use the "config" folder from git repo.
We should first promote the config changes to repo, and reflect same in "config" folder in each environment.
