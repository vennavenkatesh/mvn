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
            steps
            { 
                script
                {
                    withSonarQubeEnv('sonarqube') 
                    { 
                        sh "mvn sonar:sonar"
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
