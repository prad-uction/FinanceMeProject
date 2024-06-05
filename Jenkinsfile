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

        stage('Image tag and push to DockerHub'){
            steps{
                script{
                    sh 'docker tag financebanking pradocks/bankingimage:v1'
                    sh 'docker push pradocks/bankingimage:v1'
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