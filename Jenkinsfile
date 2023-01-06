
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
                git branch: 'main', changelog: false, credentialsId: 'github', poll: false, url: 'https://github.com/vardhan6500/springboot-app.git'
            }
        }
        
        stage('Build') {
    withMaven(jdk: 'JAVA', maven: 'maven') {
        
        println "build is running"
        sh 'mvn clean package'
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

