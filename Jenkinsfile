pipeline {
    agent any

    environment {
        NETLIFY_SITE_ID = '92056af6-66f8-46c5-b1cd-d6bb81f28818'
        NETLIFY_AUTH_TOKEN = credentials('netlify-token')
    }

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

        stage('Deploy') {
            
            agent {
                
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }

            steps {
                
                sh '''
                    npm install netlify-cli
                    node_modules/.bin/netlify --version
                    echo "Deploying to production. Site ID: $NETLIFY_SITE_ID"
                    node_modules/.bin/netlify status
                '''
            }
        }
        
        
    }
}
