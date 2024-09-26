pipeline {
        agent any
        stages {
                stage ("pull code from github"){
                        steps{
               git branch: 'main', url: 'https://github.com/Dharmendrasingh9760/psv-restaurant-1.git'
                        }
                }
                stage('Remove Old Containers and Images') {
                    steps {
                      script {
                    sh '''
                    sudo docker stop nginx  || true
                    sudo docker rm nginx || true
                    '''
                    sh '''
                    sudo docker rmi nginx:latest || true
                    '''
                }
            }
        }
               
            
                stage ("Building docker image"){
                        steps{
                                sh 'sudo docker build -t nginx:latest .'
                        }
                }
                
                stage ("Testing the Build"){
                        steps{
                                sh 'sudo docker run -dit --name node-js -p 8081:80 nginx:latest'
                                
                        }
                }


        }
}
