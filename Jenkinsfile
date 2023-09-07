pipline{
    agent any
    tools{
        maven 'mavenA'
    }
     parameters {
              string(name: 'tomcat_staging',defaultValue: '54.153.158.154', description: 'Remote Staging Server')
}                  

    stages{
        stage ('Build') {
            steps{
                sh 'mvn clean package'
            }

            post {
                success {
                     echo 'Archiving the artifacts: '***/target/*.war'
                     archiveArtifacts artifacts: '**/target/*.war'
               }
         }
      
      }
          
        stage ('Deploy to tomcat server') {
            parallel{
                stage ("Deploy to Staging") {
                   steps {
                    sh "scp -v -o StrictHostKeyChecking=no **/*.war root@${params.tomcat_staging):/home/ec2-user/apache-tomcat-8.5.93 /webapps/"
            }
        }
      }
    }
  }
}

    

    

