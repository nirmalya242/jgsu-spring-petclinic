pipeline {
    agent any
    triggers{pollSCM('* * * * *')}
    stages {
    //implicit checkout from repo
//        stage('checkout'){
//             steps{
//                 // Get some code from a GitHub repository
//                 git branch: 'main', credentialsId: 'f1296e4d-f1c0-48a5-96d6-8a5c8167cbce', url: 'https://github.com/nirmalya242/jgsu-spring-petclinic.git'
//             }
//        }
        stage('Build') {
            steps {
                // Run Maven on a Unix agent.
               // sh "mvn -Dmaven.test.failure.ignore=true clean package"
               bat 'mvnw clean package'

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }


        }
     }
     post {
             // If Maven was able to run the tests, even if some of the test
             // failed, record the test results and archive the jar file.
             always {
                 junit '**/target/surefire-reports/TEST-*.xml'
                 archiveArtifacts 'target/*.jar'
                     }
     }
}
