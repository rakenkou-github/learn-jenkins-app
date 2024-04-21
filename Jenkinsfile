pipeline {
    agent any

    stages {
        
        stage('Build') {
            
            agent {
                
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                
                sh '''
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
                '''
            }
        }
        
        /*
        stage('With Docker') {
            
            agent {
                
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            
            steps {
                echo "With Docker"
                sh '''
                    node --version
                    touch configure-yes.txt
                    ls -la
                '''
            }
        }
        */
    }
}
