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
                sh 'docker run -itd --name CBS -p 8082:8081 financebanking'
            }
        }

        stage('Image tag and push to DockerHub'){
            steps{
                script{
                    withCredentials([usernamePassword(credentialsId: 'DockerHub-credentials', passwordVariable: 'Docking-possible4Pradee', usernameVariable: 'pradeepkumarg97.19@gmail.com')])
                    sh 'docker tag financebanking pradocks/bankingimage:v1'
                    sh 'docker push pradocks/bankingimage:v1'
                }

            }
        }


   }
}
