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
                    echo $waitForQualityGate()
                }
                
                //def qualitygate = waitForQualityGate()
                //if (qualitygate.status != "OK")
                //{
                  //      error "Pipeline aborted due to quality gate coverage failure: ${qualitygate.status}"
                //}
                
            }
        }
        stage('Deploy') { 
            steps {
                echo 'deploy'
                // 
            }
        }
    }
}
