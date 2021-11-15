pipeline {
    agent {
        docker {
            image 'maven:3.8.1-adoptopenjdk-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    options {
        ansiColor('xterm')
    }
    ansiColor('css') {
         sh "ls -al"
    }

echo 'this will be rendered as-is'
// multiple ansiColor steps within one pipeline are also supported

    ansiColor('vga') {
        echo '\033[42m\033[97mWhite letters, green background\033[0m'
        }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -Dstyle.color=always -Djansi.force=true -DskipTests  clean package'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
