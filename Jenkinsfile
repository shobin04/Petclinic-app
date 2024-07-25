pipeline {
    agent any
    
    stages {
        stage ('SCM checkout') {
           steps {
               git branch: 'main', url: 'https://github.com/shobin04/Petclinic-app.git'
            }
        } 
    }
}
