pipeline{
    agent any

    tools{
        jdk 'Java21'
        maven 'Maven3.9.11'

    }

    stages{
        stage('Show message'){
            steps{
                bat 'echo "Primer stage del pipeline"'
                bat 'echo "A continuación hacemos checkout del proyecto"'

            }

        }

        stage('Ckeckout proyecto'){
                    steps{
                        git branch: 'master',
                            url: 'https://github.com/PabloGMOEducastur/biblioteca.git'

                    }

                }

    stage('Maven clean'){
                        steps{
                            bat 'mvn clean'

                        }

                    }




    }

}