pipeline {
    agent any
            tools{
                maven 'local_maven'
                 }
        stages {
            stage('Checkout') {
                steps {
                        git branch: 'master', credentialsId: 'github', url: ''
                    }
                            }
            stage('Build') {
                steps {
                    sh 'mvn clean package'
                    }
                            }
            stage('Push') {
                steps {
                    echo 'This is Push Stage'
                        }
                        }
            stage('Deploy') {

                steps {
                   sshagent(['tomcat']){
                    sh 'rsync /var/lib/jenkins/workspace/deploy_tomcat/target/*.war ec2-user@3.111.214.108:/opt/tomcat/apache-tomcat-9.0.87/webapps/'
                    }
                            }
                            }
            }
        }
