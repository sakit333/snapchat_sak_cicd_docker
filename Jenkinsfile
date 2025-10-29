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
                script {
                    def loggedIn = sh(
                        script: 'docker info 2>/dev/null | grep "Username:" || true',
                        returnStdout: true
                    ).trim()

                    if (loggedIn) {
                        echo "✅ Already logged in to DockerHub as ${loggedIn.split(":")[1].trim()}"
                    } else {
                        echo "🔐 Not logged in — asking for password..."
                        def userInput = input(
                            id: 'dockerLoginInput', message: 'Enter your DockerHub password:',
                            parameters: [password(defaultValue: '', description: 'DockerHub password', name: 'DOCKER_PASS')]
                        )

                        sh """
                            echo '${userInput}' | docker login -u sakit333 --password-stdin
                        """
                    }
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