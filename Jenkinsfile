pipeline {
    agent any

    tools {
        maven 'Maven' // Must match your Jenkins Maven installation name
        jdk 'JDK11'   // Must match your Jenkins JDK installation
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/yogi7302/JenkinsBuilt.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run') {
            steps {
                sh 'java -cp target/HelloJenkins-1.0-SNAPSHOT.jar com.example.App'
            }
        }
    }

    post {
        success {
            echo 'Build and run completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
