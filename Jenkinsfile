pipeline {
    agent any

    stages {
        
        stage('Without Docker') {
            steps {
                cleanWs()
                sh '''
                    echo "Without Docker"
                    touch configure-no.txt
                    ls -la
                '''
            }
        }
        
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
    }
}
