pipeline {
	enviroment{
	tag= "test"
	}
	
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId:'cb46df6e-b140-4439-8b9f-f4ceef31edce', url: 'http://git-server/user/repository.git']]])
            }
        }
        stage('Docker Build') {
            steps {
                sh docker build --network=host -t Jenkins_task
            }
        }
        stage('Push') {
            steps {
                sh docker login localhost:8081 --username admin --password admin123
				sh docker puush Jenkins_task
            }
        }
    }
}