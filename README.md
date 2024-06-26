# nexus

### Nexus is a Artifactory reposistory, which can be used to store and retrive the builf artifacts whenever we required, It can be also used to store the artifacts from any languages, apart from java project

## what is the diff b/w gitHub and nexus?
gitHub is a source code management
Nexus is an artifactory REPO

### Prerequists of the Nexus
1. JRE java --> version: JRE 8 or JDK 8 (JRE 11 doesnt work) --> sudo yum install java-11-amazon-corretto-devel
2.  4 gb ram minimum

### configuring the nexus
|||
|:---:|:---:|
get the latest vesion from | https://help.sonatype.com/en/download.html
download in OPT directory |
create the *nexus* user |(useradd nexus)
give sudoers permissions | (visudo file) nexus ALL=(ALL) NOPASSWD: ALL
change the owner and group for the files nexus and sonatype-work |
open nexus.rc file in bin and update the file change to | run_as_user="nexus", we are going to run the nexus server with the *nexus user*
run the nexus as a service | sudo ln -s /opt/nexus-3.15.2-01/bin/nexus /etc/init.d/nexus
switch to the nexus user | sudo su - nexus
chang ethe IP and port of nexus | sudo vi /opt/nexus/etc/nexus-default.properties
restrt the service | sudo service nexus restart
enable the nexus user | sudo systemctl enable nexus
start the nexus user | sudo systemctl start nexus
status the nexus user | sudo systemctl status nexus
login to nexus user | sudo cat /opt/sonatype-work/nexus3/admin.password
login password for nexus upto 3.15 version | username is admin pass: admin123 but later version the passwprd is stored in the admin.password file

### what are the direcotries in nexus
|name|usage|
|:---:|:---:|
etc | configurations files
lib |
bin | binary files

### create the repo in nexus

### integrate nexus repos with maven project

### upload artifacts into nexus repo
