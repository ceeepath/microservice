pipeline {
    agent any
    environment {
        SCANNER_HOME = tool 'sonarscanner'
        DOCKER_TAG = "1.0.${BUILD_NUMBER}"
   }

    stages {
            stage('SonarQube') {
             steps {
                withSonarQubeEnv('sonarscanner') {
                    sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=microservice -Dsonar.ProjectName=microservice -Dsonar.java.binaries=.'''
                }
            }
        }
            stage('adservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir('/var/lib/jenkins/workspace/microservice/src/adservice/') {
                        sh "docker build -t ceeepath/adservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/adservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/adservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('cartservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/cartservice/src/") {
                        sh "docker build -t ceeepath/cartservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/cartservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/cartservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
       }
            stage('checkoutservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/checkoutservice/") {
                        sh "docker build -t ceeepath/checkoutservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/checkoutservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/checkoutservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('currencyservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/currencyservice/") {
                        sh "docker build -t ceeepath/currencyservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/currencyservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/currencyservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }

            }
            stage('emailservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/emailservice/") {
                        sh "docker build -t ceeepath/emailservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/emailservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/emailservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('frontend') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/frontend/") {
                        sh "docker build -t ceeepath/frontend:${DOCKER_TAG} ."
                        sh "docker push ceeepath/frontend:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/frontend:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
            stage('loadgenerator') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/loadgenerator/") {
                        sh "docker build -t ceeepath/loadgenerator:${DOCKER_TAG} ."
                        sh "docker push ceeepath/loadgenerator:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/loadgenerator:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
            }
             stage('paymentservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/paymentservice/") {
                        sh "docker build -t ceeepath/paymentservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/paymentservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/paymentservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('productcatalogservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/productcatalogservice/") {
                        sh "docker build -t ceeepath/productcatalogservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/productcatalogservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/productcatalogservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('recommendationservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/recommendationservice/") {
                        sh "docker build -t ceeepath/recommendationservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/recommendationservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/recommendationservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
             }
             stage('shippingservice') {
              steps {
               script {
                 withDockerRegistry(credentialsId: 'dockerpass', toolName: 'docker') {
                    dir("/var/lib/jenkins/workspace/microservice/src/shippingservice/") {
                        sh "docker build -t ceeepath/shippingservice:${DOCKER_TAG} ."
                        sh "docker push ceeepath/shippingservice:${DOCKER_TAG}"
                        sh "docker rmi ceeepath/shippingservice:${DOCKER_TAG}"
                        sh 'docker system prune -a -f --volumes'
                    }
                }
            }
        }
      }
      stage('aws-authenticate') {
              steps {
                script {
               withAWS(credentials: 'aws_credentials', region: 'us-east-1') {
                    dir("/var/lib/jenkins/workspace/microservice/") {
                        sh 'aws eks --region us-east-1 update-kubeconfig --name class-eks-cluster'
                        // Replace the placeholder in the deployment.yaml file with the actual DOCKER_TAG value (edit in place)
                        sh """
                            sed -i 's|IMAGE_TAG|${DOCKER_TAG}|g' deployment.yaml
                        """
                        sh 'kubectl apply -f deployment.yaml'
                        sh 'sleep 20'
                        sh 'kubectl get pod'
                        sh 'kubectl get svc'
                    }
                }
            }
        }
      }
    }
    post {
        always {
            echo "Pipeline completed!"
    }
  }
}
