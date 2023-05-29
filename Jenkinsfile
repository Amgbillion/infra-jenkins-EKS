pipeline {
    agent any
   
    environment {
        AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
        AWS_DEFAULT_REGION = "eu-west-2"
    }
    stages {
        stage('Checkout') {
            steps {
           git branch: 'main', url: 'https://github.com/ooghenekaro/infra-jenkins.git'
  
            }
        }
    
        stage ("terraform init") {
            steps {
                sh ("terraform init") 
            }
        }
        
        stage ("plan") {
            steps {
                sh ("terraform plan") 
            }
        }

        stage (" Action") {
            steps {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve') 
           }
        }
    }
}
    
