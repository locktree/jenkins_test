#!/usr/bin/env groovy

/*
 * // ----------------------------------------------------------------------
 * // Simple Jenkinsfile example
 * // ----------------------------------------------------------------------
 * // A typical Continuous Delivery pipeline could look as follows:
 * // 1. Checkout from version control
 * // 2. Build
 * // 3. Unit tests
 * // 4. Integration tests
 * // 5. Static code analysis
 * // 6. Deployment in a staging environment
 * // 7. Functional and/or manual tests
 * // 8. Deployment in production
 * // ----------------------------------------------------------------------
 * // PAGE: http://localhost:9090/
 * // REPO: https://github.com/locktree/jenkins_test/
 * // TXT : /home/mitchell/Downloads/JENKINS.txt
 * // ----------------------------------------------------------------------
 */

pipeline {
    agent any

    options {
        // Check options: https://www.jenkins.io/doc/pipeline/steps/
        timestamps()
        retry(3)
        ansiColor("xterm")
        timeout time:10, unit:'MINUTES'
        timeout(time: 3, unit: "SECONDS")

        buildDiscarder(logRotator(numToKeepStr:'5'))   // Only keep the 10 most recent builds
   }


    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
            }
        }
    }
}


