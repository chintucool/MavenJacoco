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
             }
        }
       stage('Jacoco coverage') {
            steps {
                jacoco()
            }
        }
        //stage("Quality Gate") {
          //  steps {
            //    timeout(time: 1, unit: 'HOURS') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
              //      waitForQualityGate abortPipeline: true
                //}
            //}
        //}
    }
}
