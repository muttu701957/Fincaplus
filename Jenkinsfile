pipeline {
    agent any
    stages {
        stage('Checkout Code from GitHub') {
            steps {
                git url: 'https://github.com/muttu701957/Fincaplus/', branch: 'main'
                echo 'Git checked out from GitHub.'
            }
        }
        stage('Maven Clean') {
            steps {
                sh 'mvn clean'
                echo 'Maven clean completed.'
            }
        }
        stage('codecompile '){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting '){
            steps{
                sh 'mvn test'
            }
        }
        stage('quality Assurance'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package process'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fincaplus-image:latest .'
                echo 'Docker image built successfully.'
            }
        }
        stage("Trivy File System Scan") {
            steps {
                sh 'trivy fs --format table -o trivy-fs-report.html .'
                echo 'Trivy scan completed.'
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
        stage('Docker Run') {
            steps {
                sh 'docker run -d --name Container1 -p 8091:8091 fincaplus-image:latest'
                echo 'Docker container started.'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: '', contextName: '', credentialsId: 'Kubernetes', namespace: '', restrictKubeConfigAccess: false, serverUrl: '') {
                    sh "kubectl apply -f pod.yaml"
                    sh "kubectl apply -f deployment.yaml"
                    sh "kubectl apply -f service.yaml"
                    sh "kubectl apply -f hpa.yaml"
                    echo 'Kubernetes deployment completed.'
                }
            }
        }
    }
}
