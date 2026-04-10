pipeline {
    agent { 
        node {
            label "linux && java11"
        }
    }

    stages {
        stage("Build") {
            steps {
                script {
                    // contoh 1: loop
                    for (int i = 0; i < 3; i++) {
                        echo "Loop ke-${i}"
                    }

                    // contoh 2: variable
                    def appName = "belajar-spring"
                    echo "App: ${appName}"

                    // contoh 3: kondisi
                    def branch = env.BRANCH_NAME ?: "unknown"
                    if (branch == "main") {
                        echo "Ini branch utama, biasanya penuh tekanan"
                    } else {
                        echo "Branch ${branch}, santai dulu"
                    }

                    // contoh 4: hasil dari shell
                    def result = sh(
                        script: "echo HelloFromShell",
                        returnStdout: true
                    ).trim()

                    echo "Output shell: ${result}"
                }

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
