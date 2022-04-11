pipeline {
    agent any

    triggers {
        cron('*/5 * * * *')
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
                            )
                        ])
                    ])
                }

                echo "Texting mom... ${params.PHONE_NUMBER}"
                sh '''
                      aws sns publish --message "You're the best mom in the world!" --phone-number ${PHONE_NUMBER}
                   '''
            }
        }
    }
}
