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
                    // loop
                    for (int i = 0; i < 3; i++) {
                        echo "Loop ke-${i}"
                    }

                    // variable
                    def appName = "belajar-spring"
                    echo "App: ${appName}"

                    // kondisi
                    def branch = env.BRANCH_NAME ?: "unknown"
                    if (branch == "main") {
                        echo "Ini branch utama, biasanya penuh tekanan"
                    } else {
                        echo "Branch ${branch}, santai dulu"
                    }

                    // hasil dari shell
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
                script {
                    def data = [
                        "firstName": "Sahid",
                        "lastName" : "Haqqi"
                    ]

                    writeJSON file: "data.json", json: data

                    echo "JSON untuk Sahid Haqqi berhasil dibuat"
                }

                echo("Start Test")
                sh "./mvnw test"
                echo("Finish Test")
            }
        }

        stage("Deploy") {
            steps {
                echo("Start Deploy")
                sh "echo Deploying application for Sahid Haqqi..."
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
