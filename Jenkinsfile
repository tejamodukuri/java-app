node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
git credentialsId: 'jenkins-credentials', url: 'https://github.com/tejamodukuri/java-app.git'
   }
   stage('Build') {
     withMaven(jdk: 'java', maven: 'apache-maven') {
       sh 'mvn clean compile'
     }
   }
   stage('Unit Test') {
     withMaven(jdk: 'java', maven: 'apache-maven') {
       sh 'mvn test'
     }
   }
   stage('SonarQube Analysis') {
      //def job = build job: 'SonarJob'
      //withSonarQubeEnv("SonarQube") {
     withMaven(jdk: 'java', maven: 'apache-maven') {
        sh 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
          ' -Dsonar.host.url=https://sonarcloud.io '+
          ' -Dsonar.organization=pavants52 ' +
         ' -Dsonar.login=f540443177992898ca50fb418f28d763e9cbd20e ' 
        }
      //}
     }
    stage('Archival') {
     withMaven(jdk: 'java', maven: 'apache-maven') {
       sh 'mvn package'
     }
   }
     stage('Deploy to Artifactory Repo') {
     withMaven(jdk: 'java', maven: 'apache-maven') {
     }
     }
   
    stage('Deploy to Dev') {
     withMaven(jdk: 'java', maven: 'apache-maven') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }
    }
   stage('Smoke Test Execution') {
     withMaven(jdk: 'java', maven: 'apache-maven-3.5.3') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }
   }
    
   stage('Smoke Test Execution') {
     withMaven(jdk: 'java', maven: 'apache-maven-3.5.3') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
    }
   }
}
