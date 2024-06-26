# nexus

### Nexus is a Artifactory reposistory, which can be used to store and retrive the builf artifacts whenever we required, It can be also used to store the artifacts from any languages, apart from java project

## what is the diff b/w gitHub and nexus?
gitHub is a source code management
Nexus is an artifactory REPO

### Prerequists of the Nexus
1. JRE java --> version: JRE 8 or JDK 8 (JRE 11 doesnt work) --> sudo yum install java-11-amazon-corretto-devel
2.  4 gb ram minimum

### configuring the nexus
1. get the latest vesion from https://help.sonatype.com/en/download.html
2. download in OPT directory
3. create the *nexus* user (useradd nexus)
4. give sudoers permissions (visudo file) nexus ALL=(ALL) NOPASSWD: ALL
5. change the owner abd group for the files nexus and sonatype-work
6. 
 
