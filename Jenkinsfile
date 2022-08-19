node('built-in') 
{
    stage('continuosdownload') 
    {
    git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continuosbuild')
    {
    sh 'mvn package'
    }
    stage('continuosdeployment')
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline1/webapp/target/webapp.warubuntu@172.31.29.254:/var/lib/tomcat9/webapps/testapp.war'
    }
    stage('continuostesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    stage('continuosdelivery')
    {
        input message: 'Need approval from the DM!', submitter: 'srinivasu'
        sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline1/webapp/target/webapp.warubuntu@:172.31.27.175/var/lib/tomcat9/webapps/prodapp.war'
    }
    
}
