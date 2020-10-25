pipeline {
    agent any 
    stages {
        stage('Checkoutcode') { 
            steps {
                echo 'Checkoutcode'
                git 'https://github.com/vennavenkatesh/mvn.git'
                
                // 
            }
        }
        stage('sonarqube') 
        { 
            steps{
                
                script{
                withSonarQubeEnv('sonarqube') { 
                sh "mvn sonar:sonar"
                }
                timeout(time: 1, unit: 'HOURS') {
                def qg = waitForQualityGate()
                if (qg.status != 'OK') {
                    error "Pipeline aborted due to quality gate failure: ${qg.status}"
                }
              }
                
            }
        }
        stage('Create artfact') { 
            steps {
                echo 'creating artfact'
                sh "mvn clean install"
                // 
            }
        }
    }
}
