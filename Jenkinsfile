pipeline
{
    agent any
    stages
    {
        stage('continuousdownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('continuousbuild')
        {
            steps
            {
                sh 'mvn package'  
            }
        }
        stage('continuousdeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '4269195b-34f3-40cb-83ab-fe09817e7b96', path: '', url: 'http://172.31.7.83:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        stage('continuoustesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            
                sh 'java -jar /var/lib/jenkins/workspace/declrativepipeline1/testing.jar'
            }
        }
        stage('continuousdelivery')
        {
            steps
            {
               
            
                deploy adapters: [tomcat9(credentialsId: '4269195b-34f3-40cb-83ab-fe09817e7b96', path: '', url: 'http://172.31.14.181:8080')], contextPath: 'myprodapp', war: '**/*.war' 
            }
        }
    }
}

