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
  -Dsonar.projectKey=maven-new-itraindemo \
  -Dsonar.organization=itraindemo \
  -Dsonar.host.url=https://sonarcloud.io \
  -Dsonar.login=c567be076b2417e27020473ece2a6cf24b17dd33'    
       }
   } 
   stage('Archive to Jfrog') {
   } 
   stage('Docker Image') {
   } 
   stage('Deploy to Prods') {
   } 
}
