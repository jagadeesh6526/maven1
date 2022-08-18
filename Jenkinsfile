node('built-in')
{
    stage('ContinuesDownload')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    } 
    stage('ContinuesBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuesDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'd2e49ea0-a00f-459f-8b56-b7decb7fe915', path: '', url: 'http://172.31.32.153')], contextPath: 'mytestapp', war: '**/*.war'
    }
    stage('ContinuesTesting')
    {
        git credentialsId: 'd2e49ea0-a00f-459f-8b56-b7decb7fe915', url: 'https://github.com/intelliqittrainings/FunctionalTesting.git'    
        sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline11/testing.jar'
    }
    stage('ContinuesDelivery')
    {
        input message: 'delivery approval', submitter: 'jagadeesh'
        deploy adapters: [tomcat9(credentialsId: 'd2e49ea0-a00f-459f-8b56-b7decb7fe915', path: '', url: 'http://172.31.39.46:8080')], contextPath: 'mydepapp', war: '**/*.war'
    }
}
    
    
