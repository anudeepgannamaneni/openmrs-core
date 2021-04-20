node ('maven') {

   stage('SCM') {
      // git clone
	  git branch: 'master', url: 'https://github.com/anudeepgannamaneni/openmrs-core.git'
   }
   stage('BUILD '){
      //build using maven
      sh 'mvn clean install -DskipTests'
   }
   stage('repots'){
      //all reopts 
      junit 'target/surefire-reports/*.xml'
   }
    stage('SonarQube analysis') {
    withSonarQubeEnv('sonarqube-6.7') { // You can override the credential to be useddd
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
    }
  }


}