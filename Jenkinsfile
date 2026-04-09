pipeline {
    agent { 
        node {
            label "linux-agent-1 && agent"
        }
    }

    stages {
        stage('build') {
            steps {
                echo 'Hello world'
            }
        }

        stage('test') {
            steps {
                echo 'Hello test'
            }
        }

        stage('deploy') {
            steps {
                echo 'Hello deploy'
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
