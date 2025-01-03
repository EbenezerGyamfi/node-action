Pipeline{
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