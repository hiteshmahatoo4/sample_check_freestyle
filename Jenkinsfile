node {
  tools {
     maven 'Apache Maven 3.6.3'
    }
  stage('SCM') {
    git 'https://github.com/hiteshmahatoo4/sample_check_freestyle.git'
  }
  stage('SonarQube analysis') {
    withSonarQubeEnv() { // Will pick the global server connection you have configured
      sh 'mvn -f MyWebApp/pom.xml sonar:sonar'
      sh './gradlew sonar \
  -Dsonar.projectKey=sample_check_freestyle_key \
  -Dsonar.host.url=http://192.168.0.102:9000 \
  -Dsonar.login=squ_d6daa867dc5c611116c639dbc70bdf0f8d4a08d4'
    }
  }
}
/*
node {
  agent any

    
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    withSonarQubeEnv(sonarqube) {
      
      sh "./gradlew sonar"
    }
  }
    
}
*/
/*pipeline {
    agent any

    tools {
     maven 'Apache Maven 3.6.3'
    }
  
    stages {
       
        
        stage ('Code Quality') {
        steps {
            withSonarQubeEnv('sonarqube') {
            sh 'mvn -f MyWebApp/pom.xml sonar:sonar'
            }
      }
    }

        stage ('Scan using Gradle') {
            steps {
                withSonarQubeEnv(installationName: 'SonarQubeScanner', credentialsId: 'SonarQubeSecret') {
                    sh "./gradlew sonar \
                    -Dsonar.projectKey=sample_check_freestyle \
                    -Dsonar.host.url=http://192.168.51.117:9000 \
                    -Dsonar.login=sqp_e253be031c897b0f41ee86806cc340b82777f432" 
                }
            }
        }   
        
    }
}*/
