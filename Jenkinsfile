/* Import shared Library */
@Library('Matsiaze-shared-library') _

pipeline {
    environment {
      IMAGE_NAME = 'icwebapp-jenkins'
      IMAGE_TAG = 'latest'
    }
    agent none
    stages {
        stage('Build ic-webapp Image') {
            agent any
            steps {
                sh 'docker build -t mclab7/${IMAGE_NAME}:${IMAGE_TAG} app/'
            }
        }
        stage('Run Container') {
            agent any
            steps {
               script {
                 sh '''
                   docker rm -f ${IMAGE_NAME}
                   docker run -d --name ${IMAGE_NAME} -e PORT=8080 -p 5000:8080 mclab7/${IMAGE_NAME}:${IMAGE_TAG}
                   sleep 10
                 '''
               }
            }
        }
        stage('Test Image') {
            agent any
            steps {
                sh 'curl http://192.168.56.9:5000 | grep -q -i "ic webapp"'
            }
        }
        stage('Clean Container') {
            agent any
            steps {
               script {
                 sh '''
                   docker stop ${IMAGE_NAME}
                   docker rm ${IMAGE_NAME}
                 '''
               }
            }
        }
    }
  post {
    always {
      script {
	slackNotifier currentBuild.result
      }
    }
  }
}
