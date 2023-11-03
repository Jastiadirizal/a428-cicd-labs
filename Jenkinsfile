node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000'){
        stage('Build') {
            checkout scm
            sh 'npm install'
        }
        stage('Test') { 
        sh './jenkins/scripts/test.sh' 
        }
         stage('Manual Approve') {
            input message: 'Lanjutkan ke tahap deploy? (klik "process" untuk mendeploy)'
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            sleep(time: 60, unit: 'SECONDS')
        }
    }
}