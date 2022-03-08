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
                        mvn test jacoco:report
                    """
             }
        }
       stage('Jacoco coverage') {
            steps {
                jacoco(
                        execPattern: '**/jacoco.exec',
                        classPattern: '**/classes',
                        sourcePattern: '**/src/main/java',
                        inclusionPattern: '**/*.java'
                )
            }
        }  
    }
}
