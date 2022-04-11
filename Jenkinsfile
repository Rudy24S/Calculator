def groovyScript

BASE_URL = 'https:...'
pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage("init") {
            steps {
                script {
                    groovyScript = load "script.groovy"
                }
            }
        }
        stage("build") {
            steps {
                script {
                    groovyScript.buildApp()
                }
            }
        }
        stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                script {
                    groovyScript.testApp()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    groovyScript.deployApp()
                }
            }
        }
    }
}