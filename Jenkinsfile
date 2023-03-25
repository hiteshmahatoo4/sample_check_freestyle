pipeline {
    agent any

    tools {
     maven 'Apache Maven 3.6.3'
    }
  
    stages {
       stage ('Build') {
         steps {
              sh 'mvn clean install -f MyWebApp/pom.xml'
            }
        }
        
        stage ('Code Quality') {
        steps {
            withSonarQubeEnv('sonarqube') {
            sh 'mvn -f MyWebApp/pom.xml sonar:sonar'
            }
      }
    }
        stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv() {
      sh "./gradlew sonar"
    }
  }

        stage ('Scan using Gradle') {
            steps {
                withSonarQubeEnv(installationName: 'SonarQubeScanner', credentialsId: 'SonarQubeSecret') {
                    sh "./gradlew sonar \
                    -Dsonar.projectKey=sample_check_freestyle \
                    -Dsonar.host.url=http://192.168.0.106:9000 \
                    -Dsonar.login=sqp_e253be031c897b0f41ee86806cc340b82777f432" 
                }
            }
        }   
        
    }
}
