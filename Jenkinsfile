/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t bayo72/bayo_devops:' + env.BRANCH_NAME + '-0.1 .'
            }
        }
        stage('Login to Dockerhub') {
            steps {
                withCredentials([string(credentialsId: 'dockerhub_PWD', variable: 'dockerhub_pwd')]) {
                /* groovylint-disable-next-line GStringExpressionWithinString */
                sh 'docker login -u bayo72 -p ${dockerhub_pwd}' }
            }
        }
<<<<<<< HEAD
        stage('Push Image to Dockerhub') {
=======
        stage("Push Image to Dockerhub") {
>>>>>>> 8ea3a879cb71b93241f45e83b525bbcb593210cf
            steps {
                sh 'docker push bayo72/bayo_devops:' + env.BRANCH_NAME + '-0.1' }
                  }
        stage('deploy') {
            steps {
<<<<<<< HEAD
                echo 'this is the deployment stage'
                echo 'added to dev branch'
                echo 'hello!'
=======
                sh 'docker push bayo72/bayo_devops:'+env.BRANCH_NAME+'-0.1'
        stage("deploy") {
            steps { 
                echo 'this is the deployment stage'
                echo 'added to dev branch'
                echo 'hello!'

>>>>>>> 8ea3a879cb71b93241f45e83b525bbcb593210cf
            }
        }
    }
}
