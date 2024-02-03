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
        stage('Test'){
            steps {
                echo 'Testing'
            }
        }
        stage('Deploy') {
            steps {
                sh """
                  echo " hi     again"
                  echo "$GREETING"
                """
            }
        }

        stage('check parms')
        {
            steps {
                sh """  
                  echo "Hello ${params.PERSON}"
                  echo "Biography: ${params.BIOGRAPHY}"
                  echo "Toggle: ${params.TOGGLE}"
                    echo "Password: ${params.PASSWORD}"
                """
            }

    } 
    }
    post { 
        always { 
            echo 'I will always say Hello again Narasimha!'
        }
        failure { 
            echo 'Pipeline failed!'
        }
        success { 
            echo 'I will always say when success'
        } 
    }
 }
