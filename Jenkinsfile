pipeline {
    agent { 
        node {
            label "linux-agent-1 && agent"
        }
    }

    stages {
        stage("Build") {
            steps {
                echo("Hello Build 1")
                sleep(10)
                echo("Hello Build 2")
                echo("Hello Build 3")
            }
        }

        stage("Test") {
            steps {
                echo("Hello Test 1")
                sleep(10)
                echo("Hello Test 2")
                echo("Hello Test 3")
            }
        }

        stage("Deploy") {
            steps {
                echo("Hello Deploy 1")
                echo("Hello Deploy 2")
                echo("Hello Deploy 3")
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
