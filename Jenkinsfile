pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git 'https://github.com/C2-80522/jenkins-html-demo.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_4qJnvhKQsqhStNWW6b9fOXUZd60 | /usr/bin/docker login -u amita064 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t amita064/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push amita064/mywebsite'
            }
        }
        stage ('docker rm service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 amita064/mywebsite'
            }
        }
    }
}
