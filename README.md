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
install java 8 | java 11 doesnt work with nexus https://docs.aws.amazon.com/corretto/latest/corretto-8-ug/amazon-linux-install.html
get the latest vesion from | https://help.sonatype.com/en/download.html
download in OPT directory |
change the name of sonarqube for further use and simplicity | mv /opt/nexus-3.15.2-01 /opt/nexus
create the *nexus* user |(useradd nexus)
give sudoers permissions | (visudo file) nexus ALL=(ALL) NOPASSWD: ALL
change the owner and group for the files nexus and sonatype-work | chown -R nexus:nexus /opt/nexus, chown -R nexus:nexus /opt/sonatype-work, chmod -R 775 /opt/nexus, chmod -R 775 /opt/sonatype-work
open nexus.rc file in bin and update the file change to | run_as_user="nexus", we are going to run the nexus server with the *nexus user*
run the nexus as a service | sudo ln -s /opt/nexus-3.15.2-01/bin/nexus /etc/init.d/nexus
switch to the nexus user | sudo su - nexus
chang ethe IP and port of nexus | sudo vi /opt/nexus/etc/nexus-default.properties
restrt the service | sudo service nexus restart
enable the nexus user | sudo systemctl enable nexus
start the nexus user | sudo systemctl start nexus
status the nexus user | sudo systemctl status nexus
 login from browser 8081 | nexus
signin to nexus user | sudo cat /opt/sonatype-work/nexus3/admin.password
login password for nexus upto 3.15 version | `username is admin pass: admin123` but later version the password is stored in the admin.password file

### what are the direcotries in nexus
|name|usage|
|:---:|:---:|
etc | configurations files
lib |
bin | binary files

### create the repo in nexus
1. click on the setting icon *server administration and configuration* and navigate to the settings ![image](https://github.com/bhargavsp/nexus/assets/45779321/47589a8f-b07a-4b28-914f-c60dcdadc2a5)
2. click on create repository ![image](https://github.com/bhargavsp/nexus/assets/45779321/f2d36c7b-d5a3-4d65-8b4e-a7fbb48049f3)
3. select the recipe we want to create the repository
4. we have ***snapshot and release*** option while creating the repo
5. later configure that to the pom.xml file in the maven to access the nexus and to store the artifacts in the *distributionManagement* tag ![image](https://github.com/bhargavsp/nexus/assets/45779321/604bd03c-fb6b-4386-be90-de34611bdc7d)


### all the development packages are stored in the snapshot repository and all the production packages are stored in the release repository

### integrate nexus repos with maven project

### upload artifacts into nexus repo

**NOTE:**
**Basically we dont connect the central repo, remote repo to our main *maven repo server*, we use the proxy repository installed to xonnect externally and then connect that server to the internal maven server to download the packages**

### Proxy repository 
![image](https://github.com/bhargavsp/nexus/assets/45779321/13bda18a-5b95-4dfe-948b-911fad892dee)
1. we need to configure the central repo URL when creting the remote proxy repo
2. select the maven2 (proxy) and giv ehte remote storage location as the maven central repo
3. configure that in the seting.xml file in the maven config dir under ht mirror tag

### where we can see all the cutom maven repo
In the maven user home in the mavencustomlocalrepo directory 

### Group repository
we create maven2(group) it contains mixxed (release, snapshot) and configure the remote and proxy repos in the member repositories and create the group repository. Later update the pom.xml to configure that to group URL in the repositorie tag and build it
