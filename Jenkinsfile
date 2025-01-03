pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh '''
                    npm install
                    npm run build

                    '''

                archiveArtifacts artifacts: "./dist/index.html", fingerprint: true
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
}