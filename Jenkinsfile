node {
    stage('Checkout') {
        git url: 'https://github.com/Aroarr05/spring-boot-computadoras.git', branch: 'main'
    }

    stage('Build en Docker') {
        docker.image('maven:3.6.3-jdk-13').inside('--volume /tmp/maven:/home/jenkins/.m2 --env MAVEN_CONFIG=/home/jenkins/.m2') {
            sh 'mvn clean install'
        }
    }

    stage('Post') {
        if (currentBuild.result == 'SUCCESS') {
            echo '¡Build completado exitosamente!'
        } else {
            echo 'El build ha fallado.'
        }
    }
}
