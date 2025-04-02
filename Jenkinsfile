pipeline {
    agent { label 'testkube' }

    stages {
        stage('Build') {
            steps {
                // withCredentials([usernamePassword(credentialsId: 'ACR', usernameVariable: 'ACR_USER', passwordVariable: 'ACR_PASS')])
                    // sh "echo $ACR_PASS |"  
                    sh "echo ${env.$DOCKERACCESSKEY} | docker login rv2811.azurecr.io -u admin --password-stdin"
                    echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                    sh "docker build -t  rv2811.azurecr.io/k8s/pyappv7 ."
                    sh "docker push  rv2811.azurecr.io/k8s/pyappv7"

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
