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

        stage('Deploy'){
            steps{
                echo "Deploy"
            }
        }
    }

    post{
        always{
            junit 'reports/test-results.xml'
        }
    }
}