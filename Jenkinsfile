pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/java'
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test') {
            steps {
                wrap([$class: 'Xvfb', debug: true, displayName: 99, displayNameOffset: 0, timeout: 15]) {
                    sh 'mvn test'
                }
            }
        }
        stage('Report') {
            steps {
                step([$class: 'Publisher'])
            }
        }
        stage('Post_Actions') {
            steps {
                echo 'Tests finished'
            }
        }
    }
}
