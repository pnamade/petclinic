pipeline {
	agent any
    stages {
        stage('Build on k8 ') {
            steps {           
                        sh 'pwd'
                        sh 'cp -R helm/* .'
		        sh 'ls -ltr'
                        sh 'pwd'
                        sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic  --set image.repository=az400m16acr2552528234.azurecr.io/pnamade/petclinic --set image.tag=4'
              			
            }           
        }
    }
        stage('SonarQube analysis') {
            steps {
                        withSonarQubeEnv('sonarqube-8.9') { 
                        // If you have configured more than one global server connection, you can specify its name
                        //sh "${scannerHome}/bin/sonar-scanner"
                        sh "mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=demoapp-pra"
    }
        }
}
