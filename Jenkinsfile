pipeline {
    agent any
    tools {
        maven 'Maven' // Use the name you provided in the Global Tool Configuration
    }
     stages {
            stage('Checkout') {
                steps {
                    git 'https://github.com/Mihuy1/TemperatureTestJenkins'
                }
            }

            stage('Build') {
                steps {
                    sh 'mvn clean install'
                }
            }

            stage('Test') {
                steps {
                    sh 'mvn test'
                }
            }

            stage('Code Coverage') {
                steps {
                    jacoco execPattern: '**/target/jacoco.exec'
                }
            }
        }

        post {
            always {
                junit '**/target/surefire-reports/*.xml'
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }
