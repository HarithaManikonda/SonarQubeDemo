pipeline {
    agent any
    
    tools {
        maven 'maven'
        jdk 'jdk8'
    }
    

    stages {
    
    stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Deploy to Production') {
            when {
                expression { 
                   return params.ENVIRONMENT == 'PROD'
                }
            }
            steps {
                    sh """
                    echo "deploy to production"
                    """
                }
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test' 
            }
        }
        stage('Sonar scan') {
            steps {
                sh 'mvn sonar:sonar' 
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    
    
}
