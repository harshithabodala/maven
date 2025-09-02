pipeline
{
    agent any
    stages
    {
        stage('contdownload')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('contbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('contdeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '143f7317-3058-4763-b7d7-a5e9e94cc7e0', path: '', url: 'http://18.223.21.76:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('conttesting')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline1/testing.jar'
            }
        }
        stage('contdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '143f7317-3058-4763-b7d7-a5e9e94cc7e0', path: '', url: 'http://18.221.23.229:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}
