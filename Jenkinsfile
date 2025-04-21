pipeline {
    agent any

    stages {
        stage('Checkout Code from GitHub') {
            steps {
                git url: 'https://github.com/muttu701957/Fincaplus/', branch: 'main'
                echo 'Code checked out from GitHub.'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean compile test package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fincaplus-image:latest .'
            }
        }

        stage('Push To DockerHub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: "Dockerhub",
                    usernameVariable: "DockerhubUser",
                    passwordVariable: "DockerhubPass"
                )]) {
                    sh 'echo $DockerhubPass | docker login -u $DockerhubUser --password-stdin'
                    sh "docker image tag fincaplus-image:latest ${DockerhubUser}/fincaplus-image:latest"
                    sh "docker push ${DockerhubUser}/fincaplus-image:latest"
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'Kubernetes', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {

                    sh 'kubectl apply -f deployment.yaml'
                    sh 'kubectl apply -f service.yaml'
                    sh 'kubectl apply -f hpa.yaml'
                    sh 'kubectl apply -f vpa.yaml'
                }
            }
        }
    }
}
