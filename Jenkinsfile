pipeline {
  agent { label 'tomcat-slave' }
	 
	 stages {
	      stage ('git checkout') {
		       steps {
			       git branch: 'main', url: 'https://github.com/Megha-sridhar/spark.git' 
				}
			}	
			stage ('build stage') {
			    steps {
				     sh 'mvn clean install'
				}
			}
			stage('SonarQube analysis') {
			steps{
			withSonarQubeEnv('sonarqube-8.9.9') {
			sh "mvn sonar:sonar"
			}
			}
			}
			
			
			stage ('push to artifactory') {
			    steps {
				     sleep 15
				}
			}
			stage ('deploy') {
			    steps {
				     sh 'sudo cp /home/ec2-user/jenkins-slave1/workspace/jenkins-file/target/*.war /home/ec2-user/apache-tomcat-10.0.22/webapps'
				}
			}
			}
		}
