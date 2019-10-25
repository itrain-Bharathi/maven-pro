node {
   
   stage('Code Checkout') { // for display purposes
    git credentialsId: 'mshakeer011', url: 'https://github.com/itrain-Bharathi/maven-pro.git'  
   }
   stage('Code Build') {
    withMaven(jdk: 'jdk', maven: 'maven') {
     sh 'mvn clean compile'
    }  
   }
   stage('Unit Test') {
       withMaven(jdk: 'jdk', maven: 'maven') {
        sh 'mvn test'
     }  
   }
   stage('SonarQube Analysis') {
       withMaven(jdk: 'jdk', maven: 'maven') {
       sh mvn verify sonar:sonar \
                -Dsonar.projectKey=Maven-pro \
                -Dsonar.organization=itrain-bharathi \
                -Dsonar.host.url=https://sonarcloud.io \
                -Dsonar.login=e959d32e0ba2ac95c51c943814547ddd8ff5fba9
       }
   } 
   stage('Archive to Jfrog') {
   } 
   stage('Docker Image') {
   } 
   stage('Deploy to Prods') {
   } 
}
