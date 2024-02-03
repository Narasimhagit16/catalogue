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
    // parameters {
    //     string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }

    environment{
        packageVersion=""
    }
    stages {
        stage('Get the Package Version') {
            steps {
                script{
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.Version

                }
            }
        }
        stage('Install Dependencies') {
            steps {
               sh """
                 npm install
               """
            }
        }
        stage('Build'){
            steps {
                """
                ls -la
                zip -r catalogue.zip ./* -x ".git" -x "*.zip"
                ls -ltr
                """
            }
        }

    }
    post { 
        always { 
            echo 'I will always say Hello again Narasimha!'
            deleteDr()
        }
        failure { 
            echo 'Pipeline failed!'
        }
        success { 
            echo 'I will always say when success'
        } 
    }
 }
