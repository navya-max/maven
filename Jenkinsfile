
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
             sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.19.39:/var/lib/tomcat10/webapps/testapp.war'
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
                sh 'scp /var/lib/jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.31.148:/var/lib/tomcat10/webapps/prodapp.war'
              }
           }
    }       
    }

