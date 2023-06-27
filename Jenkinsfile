pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
		stage('code checkout') {
            steps {
			      cleanWs()
                  checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Aseemakram19/java-maven-sample-war.git']])         
							
				}
        }
		stage('clean the project') {
            steps {
                sh 'mvn clean'
            }
        }
		stage('compile the project') {
            steps {
                sh 'mvn compile'
            }
        }
		stage('build and package the project') {
            steps {
                sh 'mvn test package'
	       
               
            }
        }
	    stage('docker pull and expose') {
            steps {
                sh 'sudo docker rmi  mynginx --tty=false'
                sh 'sudo docker build -t mynginx .'
	        sh 'sudo docker push aseemakram19/mynginx:latest'
            }
        }
		
		
    }
}
