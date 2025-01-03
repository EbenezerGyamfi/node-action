pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh '''
                    npm install
                    npm run build

                    '''
            }
        }

        stage('Test'){
            steps{
                sh  '''
                        npm run lint
                        npm run test
                    '''
            }
        }

        stage('Build'){
            agent{
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    npm install netlify-cli -g

                    netlify --version

                    '''
            }
        }
    }

    post{
        always{
            junit 'reports/test-results.xml'
        }
    }
}