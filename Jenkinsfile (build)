pipeline {
    agent {
        docker {
            image 'maven:3.9.5-eclipse-temurin-17-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                git branch: 'main', poll: false, url: 'https://github.com/Solnijko/application-sources.git'
                sh 'mvn clean verify'
                archiveArtifacts artifacts: 'build/libs/*.jar', followSymlinks: false
            }
        }
    }
}