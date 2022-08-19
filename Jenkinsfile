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
        deploy adapters: [tomcat9(credentialsId: 'c1748f7f-70bc-4906-8733-37ae7d141eca', path: '', url: 'http://172.31.29.254:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuostesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    stage('continuosdelivery')
    {
        input message: 'Need approval from the DM!', submitter: 'srinivasu'
        deploy adapters: [tomcat9(credentialsId: 'c1748f7f-70bc-4906-8733-37ae7d141eca', path: '', url: 'http://172.31.27.175:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    
}
