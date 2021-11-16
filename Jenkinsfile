pipeline {
    agent {
        docker {
            image 'maven:3.2'
            args '-v /root/.m2:/root/.m2'
        }
    }
    options {
        ansiColor('xterm')
    }
    stages {
        stage('Build') {
            steps {
                ansiColor('gnome-terminal') {
                  echo '\033[42m\033[97mWhite letters, green background\033[0m'
                     sh 'mvn -Dstyle.color=always -Djansi.force=true -DskipTests  clean package'
                    }

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
