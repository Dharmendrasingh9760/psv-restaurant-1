pipeline {
        agent any
        stages {
                stage ("pull code from github"){
                        steps{
               git branch: 'master', url: 'https://github.com/Dharmendrasingh9760/nodejs-helloword.git'
                        }
                }
                stage('Remove Old Containers and Images') {
                    steps {
                      script {
                    sh '''
                    sudo docker stop node-js  || true
                    sudo docker rm node-js || true
                    '''
                    sh '''
                    sudo docker rmi node-hello:latest || true
                    '''
                }
            }
        }
               
            
                stage ("Building docker image"){
                        steps{
                                sh 'sudo docker build -t node-hello:latest .'
                        }
                }
                
                stage ("Testing the Build"){
                        steps{
                                sh 'sudo docker run -dit --name node-js -p 4000:4000 node-hello:latest'
                                
                        }
                }


        }
}
