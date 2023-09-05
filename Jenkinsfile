pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_9_4') {
                    sh 'mvn clean compile'
                }
            }
        }
    }
    

        stage ('Testing Stage') {
            steps {
                withMaven(maven : 'maven_3_9_4') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven_3_9_4') {
                     'deploy adapters: [tomcat8(credentialsId: 'af300c04-859c-4be3-802c-165604a7231c', path: '', url: 'http://54.153.158.154:8088/')], contextPath: null, war: '**/*.war'
               }
            }
        }
    }
    

