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
    sh 'mvn -B -DskipTests clean package'
    }
  }
}

}
