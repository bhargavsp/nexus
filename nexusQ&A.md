## why we need to rename the nexus 3.6 to nexus name
as we need to change the path for the sonatype-work we are changing the name to nexus

### how to create the repository in nexus
1. click on service adminstration option on top and go to repositories
2. click on new repository
3. we get alot of the repository recipes to selet which type of repo we want to create

### how the maven recognizes and uploads the release and the snapshots into the nexus repository
Based on the version type in the maven file under the groupID, artifact, packaging it identifies the version keyword and uploads into the particular repository

### how to update the release package with the same version number
firstly once we have created the build artificat for the release, the next builds fails for the same version as it throws the 400 erro code, because the nexus doesnt store the artifact with the same version number as it cant update, the how to update the artificate if we got into some issue <br/>
go to server administration in the nexus and click on specific repository settings and enale ***redeploy*** as deployment policy 

### roles and resposibilites of devops engineer in the nexus?


### why do we use the chkconfig on the run_as_service setup in nexus?
follow the link: https://help.sonatype.com/en/run-as-a-service.html#chkconfig
