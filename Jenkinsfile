pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t bayo72/bayo_devops:' +env.BRANCH_NAME+ '-0.4 .'
            }
        }
        stage('Login to Dockerhub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhubPWD', variable: 'sec_docker1')]) {
                sh 'docker login -u bayo72 -p ${sec_docker1}' }
            }
        }

        stage('Test') {
            steps {
                script {
                    def response = httpRequest 'http://41.242.77.125:8000/'
                    println('Status: ' + response.status)

                    if (response.status != 200) {
                        currentBuild.result = 'ABORTED'
                        error('Endpoint return non 200 code...')
                    }
                    println('Message: Test GET http://41.242.77.125:8000/ passed')
                }
            }
        }
        stage('Push Image to Dockerhub') {
            steps {
                sh 'docker push bayo72/bayo_devops:'+env.BRANCH_NAME+'-0.4'
            }
        }
    }
}
