
pipeline {
    agent any

    stages {
        stage('build the app - npm run build') {
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                    ls -al
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -al
                '''
            }    
        }
        stage('test the app'){
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
                steps{
                    sh '''
                        test -f build/index.html
                        npm test
                        echo "all works well"
                    '''
                }
            }
    }
}
