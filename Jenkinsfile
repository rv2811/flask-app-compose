pipeline {
    agent { label 'testkube' }

    stages {
        stage('Build') {
            steps {
                sh "docker login rv2811.azurecr.io -u admin -p ${env.$DOCKERACCESSKEY}"
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                docker build -t  rv2811.azurecr.io/k8s/pyappv7 .
                docker push  rv2811.azurecr.io/k8s/pyappv7

            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
