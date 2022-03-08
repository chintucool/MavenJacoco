pipeline{
    agent any
    tools{
        maven 'maven3'
    }
    stages{
       stage('Maven Test') {
            steps{
                    sh """
                        java -version
                        mvn test jacoco:report sonar:sonar
                    """
                    withSonarQubeEnv('sonar') {
			            sh 'mvn sonar:sonar'
		            }
             }
        }
       stage('Jacoco coverage') {
            steps {
                jacoco()
            }
        }
        stage("Quality Gate") {
		steps{
			script {
				qualitygate = waitForQualityGate()                     
				if (qualitygate.status != "OK") {                         
					currentBuild.result = "UNSTABLE"                     
				}       
             		}
		}
         }
    }
}
