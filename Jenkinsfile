pipeline {
    agent any

    tools {
        maven 'maven'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building the project..."
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Build stage completed successfully.'
                }
                failure {
                    echo 'Build stage failed.'
                }
            }
        }
        stage('Docker Build the Image') {
            steps {
                echo "Building the Docker image..."
                sh 'sudo docker build -t snapchat-sak-cicd-docker .'
            }
            post {
                success {
                    echo 'Docker image built successfully.'
                }
                failure {
                    echo 'Docker image build failed.'
                }
            }
        }
        stage('Docker Login to DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-cred-id',  
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh '''
                        echo "$PASS" | docker login -u "$USER" --password-stdin
                    '''
                }
            }
    }

    }  
    post {
        always {
            echo 'This will always run after the stages are complete.'
        }
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails.'
        }
    }
}