pipeline {
    agent none

    stages {

        stage('Build') {
            agent {
                label 'build1'
            }

            steps {
                deleteDir()

                sh '''
                    git clone https://github.com/Anamika1000/git2.git
                    ls -la
                '''

                stash name: 'webpage', includes: 'Anamika1000/git2/**'
            }
        }

        stage('Deploy') {
            agent {
                label 'deploy1'
            }

            steps {
                deleteDir()

                unstash 'webpage'

                sh '''
                    sudo rm -rf /var/www/html/*
                    sudo cp -r Anamika1000/git2/* /var/www/html/
                    ls -la /var/www/html/
                '''
            }
        }
    }
}
