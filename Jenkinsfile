pipeline {
    agent { 
        node {
            label "linux-agent-1 && agent"
        }
    }

    stages {
        stage("Build") {
            steps {
                echo("Start Build")
                sh "./mvnw clean compile test-compile"
                echo("Finish Build")
            }
        }

        stage("Test") {
            steps {
                echo("Start Test")
                sh "./mvnw test"
                echo("Finish Test")
            }
        }

        stage("Deploy") {
            steps {
                echo("Start Deploy")
                sh "echo Deploying application..."
                echo("Finish Deploy")
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
