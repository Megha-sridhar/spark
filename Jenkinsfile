pipeline {
    agent { label 'tomcat-slave' } 
	
  stages {
        stage('Git checkout') {
    steps {
              git branch: 'main', url: 'https://github.com/Megha-sridhar/spark.git'
        }
    }
    stage ('Build stage') {
    steps {
         sh 'mvn clean install'
	    }
    }
    stage ('Push to Artifactory') {
    steps {
        sleep 15
		}
    }
    stage ('deploy') {
    steps { 
		    sh 'sudo cp /home/ec2-user/jenkins-slave1/workspace/cicd1/target/*.war /home/ec2-user/apache-tomcat-10.0.22/webapps'
        }

    }

    }
}
