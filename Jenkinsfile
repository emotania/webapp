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
stage('Build')
  {
    steps{
    sh 'mvn clean install'
    }
  }


  stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war tomcat@192.168.244.131:/apache-tomcat-8.5.39/webapps/webapp.war'
              }      
           }       
    }


  
}

}
