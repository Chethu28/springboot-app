pipeline {
    agent any
    
    tools {
        maven "maven3"
        
    }
    
    environment {
        registry = "chethanreddy28/springbootapp"
        registryCredentails= "docker"
        AWS_ACCESS_KEY_ID = credentials("access_key")
        AWS_SECRET_ACCESS_KEY = credentials("secret_key")
        AWS_DEFAULT_REGION="us-east-1"
    }
    

    stages {
        stage('git-clone') {
            steps {
                git branch: 'main', url: 'https://github.com/Chethu28/springboot-app.git'
            }
        }
        
        stage('maven-build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('image-build') {
            steps {
                sh 'docker build -t chethanreddy28/springbootapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('image-push') {
            steps {
                withDockerRegistry(credentialsId: 'docker2', url: 'https://index.docker.io/v1/') {
                sh "docker push  chethanreddy28/springbootapp:${BUILD_NUMBER}"
            }
        }
        }
        
        stage('helm') {
            steps {
                sh "aws eks update-kubeconfig --name demo --region us-east-1"
                sh "kubectl get po"
                #sh "helm rollback first 6"
                sh " helm upgrade first --install mychart  --set image.tag=$BUILD_NUMBER"
            }
        }
        }

    }
