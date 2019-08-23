pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
		checkout scm
	    }
	}
	stage('Build') {
	    steps {
		sh '/home/softwares/apache-maven-3.6.1/bin/mvn install'
	}
	    }
	stage('Deployment') {
	    steps {
		sh 'sshpass -p "swarna99" scp target/gamutkart.war swarna@172.17.0.3:/home/gamut/Distros/apache-tomcat-8.5.38/webapps'
		sh 'sshpass -p "swarna99" ssh swarna@172.17.0.3 "JAVA_HOME=/home/softwares/jdk1.8.0_221" "/home/softwares/apache-tomcat-8.5.43/bin/startup.sh"'
	    }
	}

    }
}
