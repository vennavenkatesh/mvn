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
                echo 'sonarqube'
                withSonarQubeEnv('sonarqube') 
                {
                    sh "mvn sonar:sonar"
                    //echo $waitForQualityGate()
                    def test = waitForQualityGate()
                    
                }
                
                //def qualitygate = waitForQualityGate()
                //if (qualitygate.status != "OK")
                //{
                  //      error "Pipeline aborted due to quality gate coverage failure: ${qualitygate.status}"
                //}
                
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
