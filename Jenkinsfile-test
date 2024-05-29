pipeline {
  agent any
  
  parameters {
    string(name: 'NAME', defaultValue: '', description: 'Enter your name')
    choice(name: 'EXPERIENCE', choices: ['less than 1', '+1', '+2', '+3'], description: 'Select your experience')
  }
  
  stages {
    stage('Print Output') {
      steps {
        script {
          def name = params.NAME
          def experience = params.EXPERIENCE
          
          echo "Your name is ${name} and you have ${experience} years of experience"
        }
      }
    }
  }
} 
