// pipeline {
//     agent any 
//     stages {
//         stage('Static Analysis') {
//             steps {
//                 echo 'Run the static analysis to the code' 
//             }
//         }
//         stage('Compile') {
//             steps {
//                 echo 'Compile the source code' 
//             }
//         }
//         stage('Security Check') {
//             steps {
//                 echo 'Run the security check against the application' 
//             }
//         }
//         stage('Run Unit Tests') {
//             steps {
//                 echo 'Run unit tests from the source code' 
//             }
//         }
//         stage('Run Integration Tests') {
//             steps {
//                 echo 'Run only crucial integration tests from the source code' 
//             }
//         }
//         stage('Publish Artifacts') {
//             steps {
//                 echo 'Save the assemblies generated from the compilation' 
//             }
//         }
//     }
// }
pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/He-man-t-D/Jenkinsfile.git']])
            }
        }
        stage('Build Docker image') {
            steps{
                script{
                    bat 'docker build -t jenkinsdocker .'
                }
            }
            
        }
        stage('Rename image tag') {
            steps{
                script{
                    bat 'docker tag jenkinsdocker hemant648/jenkinsdockerapp:img1'
                }
            }
            
        }
        stage('Push image to docker hub') {
            steps{
                script{
                    bat 'docker login'
                    bat 'docker push hemant648/jenkinsdockerapp:img1'
                }
            }
            
        }
    }
    
}
