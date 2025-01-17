pipeline{
agent any
tools{
maven 'Maven'
}
stages{
stage('Inintialize')
  {
   steps{
     sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
        ''' 
   }
  }


 stage ('Check-Git-Secrets') {
      steps {
        sh 'rm trufflehog || true'
        sh 'docker run gesellix/trufflehog --json https://github.com/cehkunal/webapp.git > trufflehog'
        sh 'cat trufflehog'
      }
    }


  
stage('Build')
  {
    steps{
    sh 'mvn clean install'
    }
  }


  stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war tomcat@192.168.244.131:/home/tomcat/apache-tomcat-10.1.34/webapps/webapp.war'
              }      
           }       
    }


  
}

}
