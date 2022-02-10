pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/kranthi5121/spock-framework.git'
            }
        }
        stage('Unit Test'){
            steps{
                script{
                def mavenhome = tool name: 'maven',type:'maven'
                sh "${mavenhome}/bin/mvn clean test"
                }
            }
        }
        stage ('publish results') {
            steps{
             publishHTML([
          allowMissing: false, 
          alwaysLinkToLastBuild: true, 
          keepAll: false, 
          reportDir: "/var/lib/jenkins/workspace/test-reports/target/surefire-reports", 
          reportFiles: "index.html", 
          reportName: 'HTML Report', 
          reportTitles: ''
          ])
            }
        }
}
    }
