
pipeline 
  agent any 
    parameters {
         choice(name: 'ENVIRONMENT' ,choices: ['QA','UAT'],description: 'pick Environment value')
}
      stages{
         stage('checkout')  {
           steps{
             checkout scm
}}
}   
        stage('Build') {
           sh 'mvn install'
}}
        stage('Deployment'){
            steps{
               script{
                if("${env.ENVIRONMENT}" == 'QA'){
                  sh 'cp /root/.jenkins/workspace/maharastra/target/maharastra.war  /root/apache-tomcat-11.0.15/webapps'
                   }
           elif ("${env.ENVIRONMENT}" == 'UAT'){
                sh 'cp /root/.jenkins/workspace/maharastra/target/maharastra.war  /root/apache-tomcat-11.0.15/webapps'
                   }
                 echo "deployment has been done!"
}
}
}


                       
