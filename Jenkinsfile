pipeline {
    agent any
    tools {
        jdk 'JDK'
        maven 'MAVEN_HOME'
    }

    stages {
        stage('GitHub project pull') {
            steps {
                git branch: 'main', url: 'https://github.com/jnallani/hello.git'
            }
            
        }
        stage('mavenbuild'){
            steps {
                bat "mvn package -Dmaven.test.skip"
            }
        }
        stage('SonarQube analysis') {
            Steps {
                withSonarQubeEnv('sonarqube-8.9.2') { 
                 sh "mvn sonar:sonar"
                 }
               }
        }     
    }
}
