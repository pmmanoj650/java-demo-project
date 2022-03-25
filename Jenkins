node('Node-1') 
{
    stage('ContinuouseDownload') 
    {
        git 'https://github.com/balajimanipi/java-pro.git'
    }
    
    stage('ContinuouseBuild') 
    {
        sh 'mvn package'
    }

    stage('ContinuouseDeployment') 
    {
    
        sh 'scp  /var/lib/jenkins/workspace/ScriptePipeline/webapp/target/webapp.war root@172.31.81.228:/var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContinuouseTesting') 
    {
        git 'https://github.com/balajimanipi/FunctionlTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptePipeline/testing.jar'
        
    }
    stage('ContinuouseDelivery') 
    {
        input message: 'Waiting for Approval from the DM', submitter: 'Ram'
       sh 'scp  /var/lib/jenkins/workspace/ScriptePipeline/webapp/target/webapp.war root@172.31.83.16:/var/lib/tomcat8/webapps/prodenv.war' 
    }
    
}