node('built-in')
{
   stage('ContinuousDownload') 
   {
    git 'https://github.com/nanidev93/ourmaven.git'
   } 
   stage('ContinuousBuild') 
   {
    sh 'mvn package'
   } 
   stage('ContinuousDeployment')
   {
    deploy adapters: [tomcat9(credentialsId: 'babda926-bbe7-4dde-9f7a-9a992ebbdb4c', path: '', url: 'http://172.31.89.221:8080')], contextPath: 'testapp', war: '**/*.war'
   } 
   stage('ContinuousTesting') 
   {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
   } 
   stage('ContinuousDelivery') 
   {
    input message: 'Need approval from Delivery manager', submitter: 'nani'
    deploy adapters: [tomcat9(credentialsId: 'babda926-bbe7-4dde-9f7a-9a992ebbdb4c', path: '', url: 'http://172.31.91.3:8080')], contextPath: 'prodapp', war: '**/*.war'
   } 

}

