pipeline {
    agent any
environment {
ACCESS_KEY = credentials('AWS_ACCESS_KEY_ID')
SECRET_KEY = credentials('AWS_SECRET_ACCESS_KEY')
}
    stages {
//         stage('Checkout') {
//             steps {
//             checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/mydevopscoach/my-tf-iac-aws-repo']]])            

//           }
//         }
        stage ('Get Directory') {
            steps {
                println(WORKSPACE)
            }
        }
        stage ("terraform init") {
            steps {
                sh ('terraform init') 
            }
        }
        
        stage ("terraform Action") {
            steps {
                // withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awscred', secretKeyVariable:'AWS_SECRET_ACCESS_KEY')]) 
               // {
                echo "Terraform action is --> ${action}"
                sh ('terraform ${action} --auto-approve') 
           }
        }
    }
}
