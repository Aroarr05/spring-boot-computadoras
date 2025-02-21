pipeline {
    agent {
        docker {
            image 'maven:3.6.3-jdk-13'
            args '--volume /tmp/maven:/home/jenkins/.m2 --env MAVEN_CONFIG=/home/jenkins/.m2'
        }
    }
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/home/jenkins"
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Aroarr05/spring-boot-computadoras.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }
    post {
        success {
            echo '¡Build completado exitosamente!'
        }
        failure {
            echo 'El build ha fallado.'
        }
    }
}
