pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['QA', 'UAT'],
            description: 'Pick Environment value'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Deployment') {
            steps {
                script {

                    if (env.ENVIRONMENT == 'QA') {

                        sh '''
                        cp /root/.jenkins/workspace/kashmir/target/kashmir.war \
                           /root/apache-tomcat-11.0.15/webapps
                        '''
                        echo "Deployment has been done on QA!"

                    } else if (env.ENVIRONMENT == 'UAT') {

                        sh '''
                        cp /root/.jenkins/workspace/kashmir/target/kashmir.war \
                           /root/apache-tomcat-11.0.15/webapps
                        '''
                        echo "Deployment has been done on UAT!"

                    } else {
                        error "Invalid environment selected!"
                    }
                }
            }
        }
    }
}
               
