pipeline {
    agent any
    stages{
        stage('Clone FinanceMeProject'){
            steps{
                git url:'https://github.com/prad-uction/FinanceMeProject.git'
            }
        }

        stage('Packaging the code'){
            steps{
                sh 'mvn clean package'
            }
        }

        stage('Docker login'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'DockerHub-credentials', passwordVariable: 'Docking-possible4Pradee', usernameVariable: 'pradeepkumarg97.19@gmail.com')]) {
                }
            }
        }

        stage('Building Docker image'){
            steps{
                script{
                    sh 'docker build -t financebanking .'
                    sh 'docker images'
                }
            }
        }

        stage('Containerization and Deployment'){
            steps{
                sh 'docker run -itd --name CBS -p 8082:8081 pradocks/bankingimage:v1'
            }
        }

   }
}
