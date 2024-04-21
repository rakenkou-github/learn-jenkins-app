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
        
        stage('Parallel Stages') {

            parallel {


                stage('Test-01') {
                    
                    steps {
                        sh '''
                            echo "Test Stage-01"
                        '''
                    }
                }

                stage('Test-02') {
                    
                    steps {
                        sh '''
                            echo "Test Stage-02"
                        '''
                    }
                }

            }
        }
        
        
    }
}
