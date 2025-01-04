pipeline {
    agent any
    
    environment{
        NETLIFY_SITE_ID = '76391675-fc97-4881-985f-15a2fb0ae2b7'
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

        stage('Tests') {
                    agent {
                        docker {
                            image 'node:18-alpine'
                            reuseNode true
                        }
                    }

                    steps {
                        sh '''
                            #test -f build/index.html
                            npm test
                        '''
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
                    echo deploying to product site ID: $NETLIFY_SITE_ID
                    node_modules/.bin/netlify status
                '''
            }
        }
    }
}