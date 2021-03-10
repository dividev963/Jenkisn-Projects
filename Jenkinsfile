pipeline { 
    agent any  
    stages { 
        stage('Checkout') { 
            steps { 
              checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'b143ae53-f8b6-4fdd-be03-1b5cb1fa31f7', url: 'https://github.com/dividev963/Jenkisn-Projects.git']]])
            }
        }
        stage('Build-2') { 
            steps { 
                 build 'BuildJob' 
            }
        }
         stage('Build-1') { 
            steps { 
                 bat 'mvn -f C:/Users/HP/.jenkins/JENKINS_HOME/workspace/Pipeline_jane1/pom.xml clean install'
            }
        }
         stage('Test') { 
            steps { 
              junit allowEmptyResults: true, keepLongStdio: true, testResults: 'target/surefire-reports/*.xml\''
            }
        }
    }
}
