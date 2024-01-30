pipeline {
    agent any
    environment {
      name = "Joker"
    }
parameters{
    string(name: 'person',defaultValue: 'riya', description: 'who are you?')
    booleanParam(name: 'latest',defaultValue: true, description: 'Is the code latest')
    choice(name: 'Environment',choices: ['dev','test','prod'],description: 'choose the environment')
    }
    stages {
        stage('Run a command') {
            steps {
                sh '''
                pwd
                whoami
                date
                touch file1
                echo "${BUILD_ID}"
                echo "${JOB_NAME}"
                echo "${name}"
                echo "${username}"
                echo "${person}"
                '''
                sleep 5
            }
        }
        stage('build') {
           environment {
            username = "King"
            }
            steps {
                sh 'echo "${name}"'
                sh 'echo "${username}"'
                sh 'echo "${Environment}"'
                sleep 5
            }
        }
        stage('deploy on test') {
            steps {
                echo 'deploy on test'
                sleep 5
            }
        }
        stage('deploy on prod') {
        input{
        message "do you want to continue?"
        ok "yes, please continue"
        }
            steps {
                echo 'deploy on prod'
                sleep 5
            }
        }   
    }
      post{
      always{
      echo "always"
     } 
      failure{
      echo "something failed"
     } 
      success{
      echo "it build successfully"
     } 
   }
}
