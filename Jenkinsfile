pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    def commitId = env.GIT_COMMIT
                    sh "docker build -t ahmednageh08/flask-demo:${commitId} ."
                }
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                script {
                    withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
                        sh "docker push ahmednageh08/flask-demo:${commitId}"
                    }
                }
            }
        }
        
        stage('Stop and Start Container') {
            steps {
                script {
                    sh "docker stop flask-app || true"
                    sh "docker rm flask-app || true"
                    sh "docker run -d -p 5000:5000 --name flask-app my-image:${commitId}"
                }
            }
        }
    }
}