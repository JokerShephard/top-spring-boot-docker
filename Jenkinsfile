pipeline {
    agent any

	tools{
		maven ''
	}

    stages {
        stage('Build') {
            steps {
				echo ' --- First stage - maven build --- '
                
				// Run Maven on a Unix agent.
                sh "./mvnw install"
				
				checkout scm
				sh './mvnw -B -DskipTests clean package'
				docker.withCredentials('dockerhub').build("jokershephard/DevOpsExercise").push()
				
                
                
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
                sh "docker build --build-arg JAR_FILE=target/*.jar -t myorg/myapp ."
            }
        }
		
		stage('Dockerize'){
			steps {
				echo ' --- second stage - Dockerize --- '
			}
		
		}


    }
}
