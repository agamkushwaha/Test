pipeline {
    agent any
    environment{
      name = "riya"
    }
    parameters{
    string(name: 'person', defaultValue: 'riya', description: 'who are you?')
    booleanParam(name: 'govn employee', defaultValue: true, description: 'are you working in govn sector')
    choice(name: 'environment', choices: ['dev','test','prod'], description: 'which environment?')
    }

    stages {
        stage('Run command') {
            steps {
                sh '''
                   ls
                   pwd
                   date
                   '''
               
            }
        }
        stage('env variable') {
            environment {
              username = "ram"
            }
            steps {
                sh 'echo "${BUILD_ID}"'
                sh 'echo "${name}"'
                sh 'echo "${username}"'
                sh 'echo "${environment}"'
            }
        }
        stage('parameters') {
            steps {
                sh 'echo "${person}"'
                
            }
        }
        stage('deploy on prod') {
            input{
             message "should we continue"
             ok "yes we should"
            }
            steps {
                echo 'deploy on prod'
            }
        }
    }
        post{
           always{
          sh 'echo "always"'
     }
           success{
          sh 'echo "success"'
     }
           failure{
          sh 'echo "failure"'
     }
   }
}
