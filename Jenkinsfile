pipeline {
    agent none

    options {
        skipDefaultCheckout()
        buildDiscarder(logRotator(numToKeepStr: '3'))
        disableConcurrentBuilds()
    }
    parameters {
        booleanParam(name: 'DEPLOY_TO_DEV', defaultValue: env.BRANCH_NAME == 'master', description: '')
        booleanParam(name: 'DEPLOY_TO_TEST', defaultValue: false, description: '')
        booleanParam(name: 'DEPLOY_TO_ACCEPT', defaultValue: false, description: '')
        booleanParam(name: 'DEPLOY_TO_PROD', defaultValue: false, description: '')
        booleanParam(name: 'SKIP_TESTS', defaultValue: false, description: '')
        booleanParam(name: 'SONAR', defaultValue: true, description: '')
        string(name: 'DOCKER_TAG', defaultValue: '', description: 'e.g. 1.0.0-130-a609246c')
    }
    triggers {
        cron('@daily')
        pollSCM('H/5 * * * *')
    }
    stages {
        stage('prepare') {
            agent any
            steps {
                echo env.DEPLOY_TO_DEV
            }
        }
    }
}