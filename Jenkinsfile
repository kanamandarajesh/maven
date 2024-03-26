node('built-in') 
{
    stage('Continuous Download') 
    {
          git 'https://github.com/kanamandarajesh/maven.git'   
    }
    stage('Continuous Build') 
    {
          sh 'mvn package'    
    }
    stage('Continuous Deployment') 
    {
          deploy adapters: [tomcat7(credentialsId: '13654fd2-69a1-41a9-84ab-8de4a4781ab7', path: '', url: 'http://192.168.199.131:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('Continuous Testing') 
    {
          git 'https://github.com/kanamandarajesh/Functional-testing.git'
    
          sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline-1/testing.jar'
    }
    stage('Continuous Delivery') 
    {
          deploy adapters: [tomcat7(credentialsId: '13654fd2-69a1-41a9-84ab-8de4a4781ab7', path: '', url: 'http://192.168.199.132:8080')], contextPath: 'prodapp', war: '**/*.war'    
    }
    
    
    
}
