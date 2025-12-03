pipeline {
    agent any
    environment {
        // docker image name
        DOCKER_IMAGE_NAME="amitksunbeam/python-test-app"

        // docker user name
        DOCKER_USER_NAME="amitksunbeam"

        // docker user auth token
        DOCKER_AUTH_TOKEN=credentials('DOCKER_AUTH_TOKEN')
    }

    stages {
        stage('scm') {
            steps {
                echo "already taken care by Jenkins"
            }
        }

        stage('prepare env') {
            steps {
                // execute a shell command
                sh 'pip3 install --break-system-package -r requirements.txt '
            }
        }

        stage('prepare docker image') {
            steps {
                sh 'docker image build -t ${DOCKER_IMAGE_NAME} .'
            }
        }

        stage('docker login') {
            steps {
                sh 'echo ${DOCKER_AUTH_TOKEN} | docker login -u ${DOCKER_USER_NAME} --password-stdin'
            }
        }
    }
}
