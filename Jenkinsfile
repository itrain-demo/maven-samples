node {
   
   stage('Code Checkout') { // for display purposes
    git credentialsId: 'githubid', url: 'https://github.com/itrain-demo/maven-samples.git'  
   }
   stage('Code Build') {
    withMaven(jdk: 'jdk', maven: 'mavn') {
     sh 'mvn clean compile'
    }  
   }
   stage('Unit Test') {
       withMaven(jdk: 'jdk', maven: 'mavn') {
        sh 'mvn test'
     }  
   }
   stage('SonarQube Analysis') {
       withMaven(jdk: 'jdk', maven: 'mavn') {
     sh 'mvn verify sonar:sonar \
  -Dsonar.projectKey=newsonarqube \
  -Dsonar.organization=itraindemo \
  -Dsonar.host.url=https://sonarcloud.io \
  -Dsonar.login=4dfa6d54572017889423aad9ac0de08453c7c69b'    
       }
   } 
   stage('Archive to Jfrog') {
   } 
   stage('Docker Image') {
   } 
   stage('Deploy to Prods') {
   } 
}
