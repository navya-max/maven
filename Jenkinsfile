
pipeline 
{
    agent any
    stages
    {
       stage('continuousdownload')
       {
        steps
         {
           git 'https://github.com/IntelliqDevops/maven.git'
         }
       }
       stage('continuousbuild')
       {
          steps
          {
              sh 'mvn package'
          }
       }
       stage('continuousdeployment')
       {
           steps
           {
             sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.18.135:/var/lib/tomcat10/webapps/testapp.war'
           }  
        }
        stage('continuoustesting')
        {
            steps
            {
               git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
            }
         } 
          stage('continuousdelivery') 
          {
              steps
              {
                sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.24.168:/var/lib/tomcat10/webapps/prodapp.war'
              }
           }
    }       
    }

