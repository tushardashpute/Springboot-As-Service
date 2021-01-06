# Springboot-As-Service

# Pre-Requisites
	Install Java
	Install GIT
	Install Maven
# Install Java, GIT, Maven
	yum install java-1.8.0-openjdk git maven -y
# Clone the code into root directory
	git clone https://github.com/Naresh240/Springboot-As-Service.git
# Building Your Application
	mvn clean install
  The executable JAR file is now available in the target directory and we may start up the application by executing the following command on the command line:
	
	java -jar target/gs-spring-boot-0.1.0.jar
# Create soft link for our Jar file
	ln -s /root/Springboot-As-Service/target/gs-spring-boot-0.1.0.jar /etc/init.d/helloworld
# Create helloworld.service file with in "/etc/systemd/system" directory
	vi /etc/systemd/system/helloworld.service
	------------------------------------------------------------------------
	[Unit]
	Description=A Spring Boot application
	After=syslog.target
	
	[Service]
	User=baeldung
	ExecStart=/root/Springboot-As-Service/target/gs-spring-boot-0.1.0.jar
	SuccessExitStatus=143 
	
	[Install] 
	WantedBy=multi-user.target
	-------------------------------------------------------------------------
# Start the springboot application as a service
	service helloworld start
# Check service status of springboot application
	service helloworld status
# Goto web UI and check output of springboot application
  http://34.238.251.171:8080/
  
  ![image](https://user-images.githubusercontent.com/58024415/103660081-31d8a300-4f93-11eb-9cb2-c132d10e4384.png)
# Stop service of springboot application
	service helloworld stop
