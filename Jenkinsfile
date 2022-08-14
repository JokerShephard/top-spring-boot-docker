pipeline {
    agent any


    stages {
        stage('Build') {
            steps {
				echo 'First stage - maven build'
                // Get some code from a GitHub repository
                git 'https://github.com/JokerShephard/top-spring-boot-docker.git'

                // Run Maven on a Unix agent.
                sh "./mvnw install"
                
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
                sh "docker build --build-arg JAR_FILE=target/*.jar -t myorg/myapp ."
            }
        }
		
		stage('Dockerize'){
			steps {
				echo 'second stage - Dockerize'
			}
		
		}


    }
}
