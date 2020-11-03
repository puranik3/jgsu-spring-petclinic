#!/usr/bin/env groovy

pipeline {
    agent any

    triggers { pollSCM('* * * * *') }

    stages {
        // stage('Checkout') {
        //     steps {
        //         // Get some code from a GitHub repository
        //         git url: 'https://github.com/puranik3/jgsu-spring-petclinic.git', branch: 'main'
        //     }
        // }
        
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }

            // post {
            //     // If Maven was able to run the tests, even if some of the test
            //     // failed, record the test results and archive the jar file.
            //     success {
            //         junit '**/target/surefire-reports/*.xml'
            //         archiveArtifacts 'target/*.jar'
            //     }
            // }
        }
    }

    post {
        success {
            junit '**/target/surefire-reports/*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}