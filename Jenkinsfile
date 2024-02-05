pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    options {
        timeout(time: 1, unit : 'HOURS')
        disableConcurrentBuilds()
        ansiColor('xterm')

    }
    parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

           booleanParam(name: 'Deploy', defaultValue: false)

    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    environment{
        packageVersion=""
        nexusURL="172.31.10.115:8081"
    }
    stages {
        stage('Get the Package Version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version

                }
            }
        }


    }
    post { 
        always { 
            echo 'I will always say Hello again Narasimha!'
            deleteDir()
        }
        failure { 
            echo 'Pipeline failed!'
        }
        success { 
            echo 'I will always say when success'
        } 
    }
 }
