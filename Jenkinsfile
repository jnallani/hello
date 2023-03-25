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
        Stage('sonarquebe test'){
        steps {
              withSonarQubeEnv('My SonarQube Server') {
                sh 'mvn clean package sonar:sonar'
              }
        }
      
    }
}
