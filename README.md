To build the jar files:
#######################
ant -f maven-build.xml mavendist

To deploy snapshot (not sign requered) 
######################################
The property "maven.snapshot.repo" must be confiurated in settings.xml. Then call

ant -f maven-build.xml maven-deploy-snapshot


To deploy release (sign requered)
#################################

1. Config your settings.xml

In the $HOME/.m2/settings.xml you need a server with the ID "newton" like:

	<servers>
		<server>
			<id>newton</id>
			<username>your user name</password>
			<password>your private password</password>
		</server>
	</servers>

and the profile gpg with these config:
	
	<profiles>
		<!-- other profiles ... -->
		<profile>
			<id>gpg</id>
			<properties>
				<gpg.keyname>your gpg key name, get it by calling "gpg --list-keys" and get the public part</gpg.keyname>
				<gpg.passphrase>your private pass phrase</gpg.passphrase>
				<maven.snapshot.repo>your snapshot repository</maven.snapshot.repo>
				<maven.release.repo>your releses repository</maven.release.repo>
			</properties>
		</profile>

	</profiles>

2. Call

ant -f maven-build.xml mavestage

That all


