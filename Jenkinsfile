pipeline {
	agent any

	environment {
		DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
		DOCKER_IMAGE = 'vyankatesh23/stock-app'
		}

	stages {
		stage('Checkout code') {
		steps {
			checkout scm
			}
		}
	
		stage('docker login') {
		steps {
			sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
	
		stage('docker build') {
		steps {
			sh 'docker build -t $DOCKER_IMAGE .' 
			}
		}
		
		stage('push image') {
		steps {
			sh 'docker push $DOCKER_IMAGE:latest'
			}
		}
	}
}
