pipeline {
    agent any

    tools {
        maven 'maven-3.9'
    }
    
    stages {
        stage('Build jar') {
            steps {
                echo 'mvn package'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    echo "Building the docker image..."
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                        sh 'docker build -t agungwidodo17/demo-app:jma-2.0 .'
                        sh "echo Agung1706 | docker login -u agungwidodo17 --password-stdin"
                        sh 'docker push agungwidodo17/demo-app:jma-2.0'
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying the application..."
                }
            }
        }
    }
}
