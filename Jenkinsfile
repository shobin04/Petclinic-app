pipeline {
    agent any
    
    stages {
        stage ('SCM checkout') {
           steps {
               git branch: 'main', url: 'https://github.com/shobin04/Petclinic-app.git'
            }
        }
        stage ('build') {
            steps {
               sh""" cd /var/lib/jenkins/workspace/Petclinic-demo/
               mvn package
               """
            }
        }  
    }
}
