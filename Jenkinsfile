pipeline
{
    agent any
    stages {
        stage ('scm checkout')
        {
            steps { git branch: 'master', url: 'https://github.com/Shridhar1210/maven-project' }
        }
    }
    stage ('execute unit test framework') 
    {
        steps withMaven(globalMavenSettingsConfig: 'b9effaca-d1ac-4ca5-b14d-02640ef59bb4', jdk: 'Local_JDK', maven: 'Local_maven', mavenSettingsConfig: '90ba7166-6e8e-4755-a132-e4d7144be628', traceability: true) 
        {
            sh 'mvn test'
        } 

     }       
}
