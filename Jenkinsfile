// pipeline{
//     agent any

//     environment {

//         PROJECTKEY= 'sample'
//         SONARURL = 'http://34.134.17.81:9000'
//         LOGIN= 'sqp_012a82ccb48a91e5277a0d8e981195d9775b452a'

//     }
      

//     stages{

//        stage("Checkout code") {
//             steps {
//               git branch: 'main', url: 'https://github.com/shivam779823/gcp-devops-jenkins-project.git'  
//             }
//         }

//        stage('Unit Tests') {
//            steps {
				
//                 sh 'pytest --cov=main test_main.py --junitxml=./xmlReport/output.xml '
//                 echo "Publish Junit"
// 				junit skipMarkingBuildUnstable: true, testResults: 'xmlReport/output.xml'
                
//             }
//         }

//        stage('Code Quality Check via SonarQube') {
//             steps {
//                 script {

//                 def scannerHome = tool 'sonarscanner';

//                 withSonarQubeEnv(credentialsId: 'sonarkey'){

//                     sh "${tool("sonarscanner")}/bin/sonar-scanner \
//                     -Dsonar.projectKey=${env.PROJECTKEY} \
//                     -Dsonar.sources=. \
//                     -Dsonar.host.url=${env.SONARURL} \
//                     -Dsonar.login=${env.LOGIN}"

//                     }
//                 }
//             }
//         }

//         stage('Quality_Gate') {
//             steps {
//                 timeout(time: 3, unit: 'MINUTES') {
//                 waitForQualityGate abortPipeline: true
//                 }
//             }
//         }
//     }
  
// }







pipeline{
    agent any

  
    stages{
        stage("main"){
            when {
                branch comparator: 'EQUALS', pattern: 'main'
                }

          
            steps{
               
                                    echo "========executing main========"
            }
            post{
                always{
                    echo "========always========"
                }
            }
        }
        stage ("test") {
                        when {
                branch comparator: 'EQUALS', pattern: 'test'
                }

            steps{
              
                                    echo "========executing b======="
            }         
        }

        stage ("not any") {
             when {
                    not { branch 'main' }
                    not { branch 'test' }
             }

             steps {
                echo " not form any branch1"
             }

        }
    }
   
}
