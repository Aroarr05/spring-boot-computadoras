pipeline {
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/home/jenkins"
    }
    agent any  // ✅ Usamos "any" en lugar de "docker"
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Aroarr05/spring-boot-computadoras.git', branch: 'main'
            }
        }
        stage('Build en Docker') {
            steps {
                script {
                    docker.image('maven:3.6.3-jdk-13').inside('--volume /tmp/maven:/home/jenkins/.m2 --env MAVEN_CONFIG=/home/jenkins/.m2') {
                        sh 'mvn clean install'
                    }
                }
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
