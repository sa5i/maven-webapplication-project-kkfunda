pipeline {
    agent any
    tools 
    {
  	maven 'maven-3.9.9'
	}

    stages {
        stage('Git checkout') 
        {
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/sa5i/maven-webapplication-project-kkfunda.git'
            }
        }
        stage('Compile')
        { 
        	steps
        	{
        	sh 'mvn clean compile'
        	}
        }
        stage('Build')
        { 
        	steps
        	{
        	sh 'mvn clean package'
        	}
        }
         stage('SQ Report')
        { 
        	steps
        	{
        	sh 'mvn sonar:sonar'
        	}
        }
         stage('Nexus')
        { 
        	steps
        	{
        	sh 'mvn deploy'
        	}
        }
       
    }
}
