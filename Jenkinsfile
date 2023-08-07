pipeline
{
    agent any
    stages {
        stage ('scm checkout')
        {
            steps {  git branch: 'master', url: 'https://github.com/Shridhar1210/maven-project' }
        }
        stage ('execute unit test framework') 
        {
            steps { withMaven(globalMavenSettingsConfig: 'b9effaca-d1ac-4ca5-b14d-02640ef59bb4', jdk: 'Local_JDK', maven: 'Local_maven', mavenSettingsConfig: '90ba7166-6e8e-4755-a132-e4d7144be628', traceability: true)}
            {
            sh 'mvn test'
            }    
        }
        stage ('Build the Code') 
        {            
            steps {withMaven(globalMavenSettingsConfig: 'b9effaca-d1ac-4ca5-b14d-02640ef59bb4', jdk: 'Local_JDK', maven: 'Local_maven', mavenSettingsConfig: '90ba7166-6e8e-4755-a132-e4d7144be628', traceability: true)}
            {
                sh 'mvn package'
            }
        }
        stage ('Deploy to Tomcat Server')
        {
            steps { sshagent(['Tomcat_PemKeyadded'])
                { sh 'scp -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.64.63.117:/usr/share/tomcat/webapps/'         
                
                }
            }
        }
}
}
