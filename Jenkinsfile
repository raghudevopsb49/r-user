pipeline {
    
    agent any

    environment {
        NEXUS = credentials('NEXUS')
        MAJOR_VERSION=1
        ITERATION_NUMBER=2
    }
    
    stages { 
        stage('NPM Install') {
            steps {
                sh label: '', script: '''
                  npm install
                '''
            }
        }

        stage('Archive') {
            steps {
                sh 'tar -czf user.tgz node_modules user.js package.json'
            }
        }

        stage('Upload Artifacts') {
            steps {
                sh '''
                VERSION="${MAJOR_VERSION}.${ITERATION_NUMBER}.${BUILD_NUMBER}"
                mv user.tgz user-${VERSION}.tgz
                curl -v -u ${NEXUS_USR}:${NEXUS_PSW} --upload-file user-${VERSION}.tgz http://3.234.236.173:8081/repository/user/user-${VERSION}.tgz
                '''
            }
        }

    }
    
}