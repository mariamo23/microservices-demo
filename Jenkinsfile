pipeline {
    agent any
    environment{
        SCANNER_HOME = tool  'sonar-scanner'
        AWS_ACCOUNT_ID="654654207831"
        AWS_DEFAULT_REGION="ca-central-1"
    }

    stages {
        stage('clean workspace'){
            steps{
                cleanWs()
            }
        }
       // stage('Git Checkout') {
         //   steps {
           //     git branch: 'dev', url: 'https://github.com/mariamo23/microservices-demo.git'
          //  }
       // }
        stage('sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
    
                sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=project -Dsonar.projectName=project -Dsonar.java.binaries=. '''
            }
                
            }
        }
        stage('Logging into AWS ECR') {
            steps {
                script {
                  withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws_cred', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]){
                        sh """aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com"""
                        }
                 } 
            }
        }
        stage('adservice') {
            steps {
                script{
                   // withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker'){
                  //sudo chmod 777 /var/run/docker.sock      
                  dir('/var/lib/jenkins/workspace/Summary_project/src/src/adservice/') {
                                sh ' docker build -t adservice .'
                                sh ' docker tag adservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/adservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/adservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/adservice:latest'
//}
}
                }
            }
        }
                stage('cartservice') {
            steps {
                script{
              //      withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/cartservice/src/') {
                                sh ' docker build -t cartservice .'
                                sh ' docker tag cartservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/cartservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/cartservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/cartservice:latest'
//}
}
                }
            }
        }
                stage('checkoutservice') {
            steps {
                script{
                 //   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/checkoutservice/') {
                                sh ' docker build -t checkoutservice .'
                                sh ' docker tag checkoutservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/checkoutservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/checkoutservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/checkoutservice:latest'
//}
}
                }
            }
        }
                stage('currencyservice') {
            steps {
                script{
             //       withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/currencyservice/') {
                                sh ' docker build -t currencyservice .'
                                sh ' docker tag currencyservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/currencyservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/currencyservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/currencyservice:latest'
//}
}
                }
            }
        }
                stage('emailservice') {
            steps {
                script{
                 //   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/emailservice/') {
                                sh ' docker build -t emailservice .'
                                sh ' docker tag emailservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/emailservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/emailservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/emailservice:latest'
//}
}
                }
            }
        }
                stage('frontend') {
            steps {
                script{
                  //  withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/frontend/') {
                                sh ' docker build -t frontend .'
                                sh ' docker tag frontend:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/frontend:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/frontend:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/frontend:latest'
//}
}
                }
            }
        }
                stage('loadgenerator') {
            steps {
                script{
                 //   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/loadgenerator/') {
                                sh ' docker build -t loadgenerator .'
                                sh ' docker tag loadgenerator:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/loadgenerator:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/loadgenerator:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/loadgenerator:latest'
//}
}
                }
            }
        }
                stage('paymentservice') {
            steps {
                script{
                 //   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/paymentservice/') {
                                sh ' docker build -t paymentservice .'
                                sh ' docker tag paymentservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/paymentservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/paymentservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/paymentservice:latest'
}
//}
                }
            }
        }
                stage('productcatalogservice') {
            steps {
                script{
                  //  withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/productcatalogservice/') {
                                sh ' docker build -t productcatalogservice .'
                                sh ' docker tag productcatalogservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/productcatalogservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/productcatalogservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/productcatalogservice:latest'
//}
}
                }
            }
        }
                stage('recommendationservice') {
            steps {
                script{
                  //  withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/recommendationservice/') {
                                sh ' docker build -t recommendationservice .'
                                sh ' docker tag recommendationservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/recommendationservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/recommendationservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/recommendationservice:latest'
//}
}
                }
            }
        }
                stage('shippingservice') {
            steps {
                script{
                   // withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        dir('/var/lib/jenkins/workspace/Summary_project/src/shippingservice/') {
                                sh ' docker build -t shippingservice .'
                                sh ' docker tag shippingservice:latest 654654207831.dkr.ecr.ca-central-1.amazonaws.com/shippingservice:latest'
                                sh ' docker push 654654207831.dkr.ecr.ca-central-1.amazonaws.com/shippingservice:latest'
                                sh ' docker rmi 654654207831.dkr.ecr.ca-central-1.amazonaws.com/shippingservice:latest'
}
//}
                }
            }
        }
        stage('release') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'ekscluster', contextName: '', credentialsId: 'k8s_cred', namespace: '', restrictKubeConfigAccess: false, serverUrl: 'https://4B7C7D7D236F9796E03CE80F4059DF74.sk1.ca-central-1.eks.amazonaws.com') {
    
                       sh 'kubectl apply -f release/kubernetes-manifests.yaml'
                        sh 'kubectl get pods'
                        sh 'kubectl get svc'
                }
            }
        } 
         
    }
}
