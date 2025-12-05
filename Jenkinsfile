pipeline {
    agent any

    tools {
        jdk 'Java21'
        maven 'Maven3.9.11'
    }

    environment {
        VERSION_BACKEND = "2.0.1"
    }

    stages {

        stage('Show message') {
            steps {
                bat 'echo "Primer stage del pipeline"'
                bat 'echo "A continuación hacemos checkout del proyecto"'
            }
        }

        stage('Checkout proyecto') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/PabloGMOEducastur/biblioteca.git'
            }
        }

        stage('Comandos Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Crear directorio') {
            steps {
                bat "mkdir v%VERSION_BACKEND%"
            }
        }

    }
}
