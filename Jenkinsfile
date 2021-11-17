peline {
    agent any
    tools {
        nodejs "node17"
    }
    environment {
        NODE_ENV='production'
    }

    stages {
        stage('Source') {
            steps {
                git branch: 'main', url: 'https://github.com/arindamgb/nodejs-app.git'
                echo 'End of Stage Source'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
                echo 'End of Stage Build'
            }
        }
        stage('saveArtifact') {
            environment {
                NODE_ENV='staging'
            }
            steps {
                archiveArtifacts artifacts: '**', followSymlinks: false
                echo NODE_ENV
                withCredentials([string(credentialsId: '9fc16e27-03a5-472b-a2b3-58b9e807adb3', variable: 'secvar')]) {
                // some block
                echo secvar
                }
            }
        }
    }
}

