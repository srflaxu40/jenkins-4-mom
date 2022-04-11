pipeline {
    agent any

    triggers {
        cron('0 21 * * *')
    }

    stages {
        stage('Send SMS') {
            steps {
              script { 
                    properties([
                        parameters([
                            string(
                                defaultValue: '+10000000000', 
                                name: 'PHONE_NUMBER'
                            ),
                            choice(
                                name: 'PERSON',
                                choices: ['mom', 'dad', 'guy'], description: ''
                            )
                        ])
                    ])
                }

                echo "Texting mom... ${params.PHONE_NUMBER}"
                sh '''
                      aws sns publish --message "You're the best ${PERSON} in the world!" --phone-number ${PHONE_NUMBER}
                   '''
            }
        }
    }
}
