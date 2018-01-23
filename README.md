# Nexus-Git Repositories 

This project contains Maven repositories for release and snapshot

To start using artifacts hosted here within your own Maven project, add the
following `<repository>` elements to an active profile defined in your Maven
[`settings.xml`][1] file:

[1]: http://maven.apache.org/settings.html

		<repositories>
			<repository>
				<id>ccmsd-releases</id>
				<name>ccmsd Releases</name>
				<url>https://github.com/naveenccmsd/Nexus-Git/raw/master/releases</url>
				<releases><enabled>true</enabled></releases>
				<snapshots><enabled>false</enabled></snapshots>
			</repository>
       
			<repository>
				<id>ccmsd-snapshots</id>
				<name>ccmsd Snapshots</name>
				<url>https://github.com/naveenccmsd/Nexus-Git/raw/master/snapshots</url>
				<releases><enabled>false</enabled></releases>
				<snapshots><enabled>true</enabled></snapshots>
			  </repository>
		</repositories>
		
To upload/deploy new artifact into local repositories.Add below into [`pom.xml`][2] file:

[2]: pom.xml

	<properties>
		<repository.path>${user.home}/Projects/Nexus-Git</repository.path>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
	</properties>
	
	<distributionManagement>
		<repository>
			<id>ccmsd-releases</id>
			<url>file://${repository.path}/releases</url>
			<uniqueVersion>false</uniqueVersion>
		</repository>
		<snapshotRepository>
			<id>ccmsd-snapshots</id>
			<url>file://${repository.path}/snapshots</url>
			<uniqueVersion>true</uniqueVersion>
		</snapshotRepository>
	</distributionManagement>
	<build>
		<pluginManagement>
			<plugins>
				<plugin>
					<artifactId>maven-release-plugin</artifactId>
					<version>2.1</version>
					<configuration>
						<autoVersionSubmodules>true</autoVersionSubmodules>
						<pushChanges>false</pushChanges>
						<localCheckout>true</localCheckout>
					</configuration>
				</plugin>
			</plugins>
		</pluginManagement>
	</build>
	

	
Steps :

1.Clone this repository into ${user.home}/Projects folder.

2.After updating pom.xml run "mvn clean deploy".(Files should uploaded into local repo${user.home}/Projects/Nexus-Git)

3.Push to remote 
	git add .
	git commit -m "msg"
	git push
	
	
