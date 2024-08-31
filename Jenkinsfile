node('built-in')
{
    stage('continuous Download')
    {
        git 'https://github.com/kanamandarajesh/maven.git'
    }
    stage('continuous Build')
    {
        sh 'mvn package'
    }
    stage('continuous Deploy')
    {
        deploy adapters: [tomcat7(credentialsId: '163a1995-8583-453d-8c5d-c57f0ae8bafe', path: '', url: 'http://192.168.199.134:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('continuous testing')
    {
        git 'https://github.com/kanamandarajesh/Functional-testing.git'
        sh 'java -jar /var/lib/jenkins/workspace/Testing/testing.jar'
    }
    stage('Continuous Delivery')
    {
        deploy adapters: [tomcat7(credentialsId: '163a1995-8583-453d-8c5d-c57f0ae8bafe', path: '', url: 'http://192.168.199.133:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
