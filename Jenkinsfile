node {
   
   stage('Code Checkout') { // for display purposes
      // Get some code from a GitHub repository
git credentialsId: '	0dffb763-3bcf-486b-b09d-65c52bf36a02', url: 'https://github.com/tejamodukuri/java-app.git'
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
        sh ' mvn sonar:sonar ' +
          ' -Dsonar.host.url=https://sonarcloud.io  '+
          ' -Dsonar.organization=tejamodukuri-github ' +
         ' -Dsonar.login=fe02b6165d5aa637b8b6991df03da3aed554937b4 ' 
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
     withMaven(jdk: 'java', maven: 'apache-maven') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
   }
   }
    
   stage('Smoke Test Execution') {
     withMaven(jdk: 'java', maven: 'apache-maven') {
      //junit '**/target/surefire-reports/TEST-*.xml'
      //archive 'target/*.jar'
    }
   }
}
