
pipeline {
    agent any

        tools {
            maven "maven3"
}
  environment {
       registry = "653158732553.dkr.ecr.ap-northeast-1.amazonaws.com/my-docker-repo"
  }
  
    stages {
        stage("checkout") {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vardhan6500/springboot-app']])
            }
        }
        stage ("Build Jar") {
            steps {
                sh "mvn clean install"
            }
        }
        stage ("Build Iamge") {
            steps {
                script {
                    docker build registry
                }
            }
        }
        }
        
    }

