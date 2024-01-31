pipeline
{
agent any
stages
{
    stage("checkout")
   {
   steps
     {
       git branch: 'main', url: 'https://github.com/nocturnaldevops/Project1.git'   
mail bcc: '', body: 'the code has been successfully checked out', cc: '', from: '', replyTo: '', subject: 'the code has been successfully checked out', to: 'nocturnaldevops@gmail.com'
      }
    }
    stage("build")
   {
   steps
     {
          sh 'mvn package'
mail bcc: '', body: 'the artifact is successfully built', cc: '', from: '', replyTo: '', subject: 'the artifact is successfully built', to: 'nocturnaldevops@gmail.com'
      }
    }
    stage("deploytotest")
   {
   steps
     {
         sh 'scp /var/lib/jenkins/workspace/cic-deployment2/target/devops.war ubuntu@172.31.18.161:/var/lib/tomcat9/webapps/testnew.war' 
mail bcc: '', body: '''the artifact is successfully deployed to test
the application is accessible on the below url
http://51.20.121.222:8080/testnew''', cc: '', from: '', replyTo: '', subject: 'the artifact is successfully deployed to test', to: 'nocturnaldevops@gmail.com'
      }
    }
    stage("runtestcases")
   {
   steps
     {
          sh 'echo "testing passed"'
mail bcc: '', body: 'tests run successfully . the application is ready to be deployed to prod', cc: '', from: '', replyTo: '', subject: 'tests run successfully . the application is ready to be deployed to prod', to: 'nocturnaldevops@gmail.com'
      }
    }
    stage("deploytoprod")
   {
   steps
     {
           sh 'scp /var/lib/jenkins/workspace/cic-deployment2/target/devops.war ubuntu@172.31.20.234:/var/lib/tomcat9/webapps/app2024.war' 
mail bcc: '', body: '''application hit the prod servers
http://13.60.4.131:8080/app2024''', cc: '', from: '', replyTo: '', subject: 'application released', to: 'nocturnaldevops@gmail.com'
      }
    }
}
post{
failure{
mail bcc: '', body: 'Project FAILED!!!', cc: '', from: '', replyTo: '', subject: 'Project FAILED!!!', to: 'nocturnaldevops@gmail.com'
}
}
}