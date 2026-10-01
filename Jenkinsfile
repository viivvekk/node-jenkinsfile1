// pipeline {
//     agent any

//     stages {

//         stage('Check Node') {
//             steps {
//                 sh 'node --version'
//                 sh 'npm --version'
//             }
//         }

//         stage('Install Backend Dependencies') {
//             steps {
//                 dir('backend') {
//                     sh 'npm ci'
//                 }
//             }
//         }

//         stage('Test Backend') {
//             steps {
//                 dir('backend') {
//                     sh 'echo No backend tests configured yet'
//                 }
//             }
//         }

//         stage('Install Frontend Dependencies') {
//             steps {
//                 dir('frontend') {
//                     sh 'npm ci'
//                 }
//             }
//         }

//         stage('Test Frontend') {
//             steps {
//                 dir('frontend') {
//                     sh 'npm run test --if-present'
//                 }
//             }
//         }

//         stage('Build Frontend') {
//             steps {
//                 dir('frontend') {
//                     sh 'npm run build'
//                 }
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Build and tests completed successfully!'
//         }

//         failure {
//             echo 'Build or tests failed.'
//         }

//         always {
//             archiveArtifacts artifacts: 'frontend/dist/**',
//                              allowEmptyArchive: true
//         }
//     }
// }
pipeline {
    agent any

    environment {
        NODE_HOME = 'C:\\Program Files\\nodejs'
        PATH = "${NODE_HOME};${env.PATH}"
    }

    stages {

        stage('Check Node') {
            steps {
                bat '''
                    echo Checking Node.js...
                    where node
                    node --version
                    npm --version
                '''
            }
        }

        stage('Install Backend Dependencies') {
            steps {
                bat '''
                    cd backend
                    npm install
                '''
            }
        }

        stage('Test Backend') {
            steps {
                bat '''
                    cd backend
                    npm test
                '''
            }
        }

        stage('Install Frontend Dependencies') {
            steps {
                bat '''
                    cd frontend
                    npm install
                '''
            }
        }

        stage('Test Frontend') {
            steps {
                bat '''
                    cd frontend
                    npm test
                '''
            }
        }

        stage('Build Frontend') {
            steps {
                bat '''
                    cd frontend
                    npm run build
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/build/**, **/dist/**', allowEmptyArchive: true
        }

        success {
            echo 'Build completed successfully!'
        }

        failure {
            echo 'Build or tests failed.'
        }
    }
}
