pipeline {
    agent any

    // environment {
    //         SONAR_RUNNER_HOME = tool 'SonarQube'
    //         PROJECT_NAME = "ansible"
    //       }
    
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
        stage('SonarQube') {
          steps {
            withSonarQubeEnv('SonarQube') {
                sh '''cd /var/lib/jenkins/workspace/Petclinic-demo/
                mvn clean verify sonar:sonar \
               -Dsonar.projectKey=ansible \
               -Dsonar.projectName='ansible' \
               -Dsonar.host.url=http://54.227.47.234/:9000 \
               -Dsonar.token=sqp_155caf8788135eacef28b1f29f54967c309d6190
              '''
             }
          }
        stage ('deploy') {
            steps {
                 sh"""sudo cp /var/lib/jenkins/workspace/JPetclinic-demo/target/petclinic.war /opt/tomcat/webapps
                 sudo systemctl restart tomcat
                 """
             }
          }       
       }
    }
}
