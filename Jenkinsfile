pipeline {
    agent { 
        node {
            label "linux-agent-1 && agent"
        }
    }

    stages {
        stage('hello') {
            steps {
                echo 'Hello world'
            }
        }
    }

    post {
        always {
            echo 'Pipeline selesai (entah sukses atau gagal, hidup tetap jalan)'
        }
        success {
            echo 'Mantap, sukses. Langka tapi terjadi'
        }
        failure {
            echo 'Gagal. Seperti ekspektasi awal'
        }
        cleanup {
            echo "Don't care success or error"
        }
    }
}
