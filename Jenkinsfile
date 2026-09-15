pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/maven.git'
            }
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment')
        {
            steps
            {
             deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'dd5e2d55-289b-4e05-adac-1648088ca888', path: '', url: 'http://13.202.43.156:8080')], contextPath: 'testingapp', war: '**/*.war'
            }   
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                sh ' java -jar  /var/lib/jenkins/workspace/Declarativepipeline1/testing.jar'
            }
        }
        stage('Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'dd5e2d55-289b-4e05-adac-1648088ca888', path: '', url: 'http://172.31.19.67:8080')], contextPath: 'prodapp', war: '**/*.war'
            }
        }
    }
}
