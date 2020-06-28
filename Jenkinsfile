#!/usr/bin/env groovy


def getShortCommitHash() {
    return sh(returnStdout: true, script: "git log -n 1 --pretty=format:'%h'").trim()
}

def getChangeAuthorName() {
    return sh(returnStdout: true, script: "git show -s --pretty=%an").trim()
}

def getChangeAuthorEmail() {
    return sh(returnStdout: true, script: "git show -s --pretty=%ae").trim()
}

def getChangeSet() {
    return sh(returnStdout: true, script: 'git diff-tree --no-commit-id --name-status -r HEAD').trim()
}

def getChangeLog() {
    return sh(returnStdout: true, script: "git log --date=short --pretty=format:'%ad %aN <%ae> %n%n%x09* %s%d%n%b'").trim()
}

def getCurrentBranch () {
    return sh (
            script: 'git rev-parse --abbrev-ref HEAD',
            returnStdout: true
    ).trim()
}

def isPRMergeBuild() {
    return (env.BRANCH_NAME ==~ /^PR-\d+$/)
}


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

                writeFile file: 'test-results.txt', text: 'hello passed'   //write file to jenkins workspace
                sh 'cat test-results.txt'

                //sh 'env | sort'
            }
        }



        // ----------------------------------------------------------------------
        //    GIT INFORMATION
        // ----------------------------------------------------------------------
 stage('Get some git information') {
     steps {
         script {
             branchName = getCurrentBranch()
             shortCommitHash = getShortCommitHash()
             //echo $branchName
	     //echo $shortCommitHash

             //something else
             PR_List = sh(
                     script: "curl https://api.github.com/repos/locktree/jenkins_test/pulls?state=closed | jq  -c -r  '.[] | .number' ",
                     returnStdout: true
             ).trim().split('\n')[0]
             print("${PR_List}")

             // something else
             if(env.BRANCH_NAME == "master") {
                   echo 'masterrrrrrrrrrrrr'
             } else {
                  echo 'not on the master'
             }

             //something else
             //try{
             //    sh 'bin/destroy.sh >> debug'
             //} catch(error) {
             //    def error_details = readFile('./debug');
             //    def message = "BUILD ERROR: There was a problem building the Base Image. \n\n ${error_details}"
             //    sh "rm -f ./debug"
             //    handleError(message)
             //}
         }
     }
 }





        // ----------------------------------------------------------------------
        //    BUILD
        // ----------------------------------------------------------------------
        stage('Build') {
            steps {
                echo 'Building..'
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
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












