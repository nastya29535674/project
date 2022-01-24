pipeline {
    agent {
        node {
            label 'node_main'
        }
    }
    stages {
        stage('Checkout code'){
            steps {
                 checkout scm
            }
       }
        stage('Build') {
            steps {
                sh '''
                cd spring_petclinic
                sudo chmod +x mvnw
                sudo ./mvnw package
                '''
            }
        }
        stage ('Delivery artifactory') {
            steps {
                sh 'sudo scp -i /home/ubuntu/.ssh/terraform.pem /home/ubuntu/jenkins/workspace/build/spring_petclinic/target/*.jar ubuntu@18.170.74.194:/home/ubuntu/artifactory/'
            }
        }
    }
}
