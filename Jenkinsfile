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

        stage('Copiar ficheros'){
            steps{
                bat 'xcopy /Y ".\\target\\*.jar" ".\\v%VERSION_BACKEND%"'
            }

            post {
                success { bat 'echo "Después de copiar los ficheros correctamente"' }
                failure { bat 'echo "ERROR copiando los ficheros"' }
                always  { bat 'echo "Se ejecuta siempre luego del stage Copiar ficheros"' }
            }
        }

    }
}

