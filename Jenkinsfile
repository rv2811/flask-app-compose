pipeline {
    agent { label 'testkube' }

    stages {
        stage('Build') {
            steps {
                script {
                        withCredentials([string(credentialsId: 'DOCKERACCESSKEY', variable: 'DOCKERACCESSKEY')])
                        {
                        sh "echo $DOCKERACCESSKEY | docker login rv2811.azurecr.io -u rv2811 --password-stdin"
                        // echo Running ${env.BUILD_ID} on ${env.JENKINS_URL}
                        sh "docker build -t  rv2811.azurecr.io/k8s/pyappv7 . --no-cache"
                        sh "docker push  rv2811.azurecr.io/k8s/pyappv7"
                        }

                    }

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
