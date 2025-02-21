pipeline {
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/home/jenkins"
    }
    agent {
        docker {
            image 'maven:3.6.3-jdk-13'
            args '--volume /tmp/maven:/home/jenkins/.m2 --env MAVEN_CONFIG=/home/jenkins/.m2'
        }
    }
    stages {
        stage('Checkout') {
            steps {
                // Clone the repository from GitHub
                git url: 'https://github.com/Aroarr05/spring-boot-computadoras.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                // Compile the project using Maven
                sh 'mvn clean install'
            }
        }
    }
    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
