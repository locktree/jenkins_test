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
 * // PAGE:     http://localhost:9090/
 * // REPO:     https://github.com/locktree/jenkins_test/
 * // TXT :     /home/mitchell/Downloads/JENKINS.txt
 * // JK File:  /home/mislotbo/rommelvak/jenkins_test/Jenkinsfile
 * // START:    java -jar ~/Downloads/jenkins.war --httpPort=9090
 * // ----------------------------------------------------------------------
 */

pipeline {
    agent any

    options {
        // Check options: https://www.jenkins.io/doc/pipeline/steps/
        timestamps()                                    // Add timestamps to the Console Output
        ansiColor("xterm")                              // Color ANSI Console Output
        timeout(time: 20, unit: "SECONDS")              // Executes the code inside the block with a determined time out limit.
        buildDiscarder(logRotator(numToKeepStr:'10'))   // Only keep the 10 most recent builds
    }


    stages {

        // ----------------------------------------------------------------------
        //    INITIALIZE
        // ----------------------------------------------------------------------
        stage('Initialize') {
            environment {
                // Some stage specific variables
                LOG='something'
            }
            steps {
                echo 'Initialize..'
            }
        }


        // ----------------------------------------------------------------------
        //    BUILD
        // ----------------------------------------------------------------------
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                sh 'printf "\\e[31mSome code compilation here...\\e[0m\\n"'
                writeFile file: 'test-results.txt', text: 'passed' 
            }
        }


        // ----------------------------------------------------------------------
        //    TEST
        // ----------------------------------------------------------------------
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }


        // ----------------------------------------------------------------------
        //    DEPLOY
        // ----------------------------------------------------------------------
        stage('Deploy') {
            steps {
                echo 'Deploying..'
            }
        }



    }
}


