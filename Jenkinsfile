pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                TOKEN=$(az acr login --name <acrName> --expose-token --output tsv --query accessToken)
                docker login rv2811.azurecr.io --username rv2811 --password-stdin <<< $TOKEN 
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
