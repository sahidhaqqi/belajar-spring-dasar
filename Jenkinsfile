pipeline {
    agent none

    environment {
        BUILD_TIME = "${new Date().format('yyyy-MM-dd HH:mm:ss')}"
    }

    stages {
        stage("Build") {
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                echo "Job: ${env.JOB_NAME} | Build: ${env.BUILD_NUMBER} | Branch: ${env.BRANCH_NAME} | Time: ${env.BUILD_TIME}"

                script {
                    for (int i = 0; i < 3; i++) {
                        echo "Loop ke-${i}"
                    }

                    def appName = "belajar-spring"
                    echo "App: ${appName}"

                    def branch = env.BRANCH_NAME ?: "unknown"
                    if (branch == "main") {
                        echo "Ini branch utama, biasanya penuh tekanan"
                    } else {
                        echo "Branch ${branch}, santai dulu"
                    }

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
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                echo "Job: ${env.JOB_NAME} | Build: ${env.BUILD_NUMBER} | Branch: ${env.BRANCH_NAME} | Time: ${env.BUILD_TIME}"

                script {
                    def data = [
                        "firstName": "Sahid",
                        "lastName" : "Haqqi",
                        "buildTime": env.BUILD_TIME
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
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps {
                echo "Job: ${env.JOB_NAME} | Build: ${env.BUILD_NUMBER} | Branch: ${env.BRANCH_NAME} | Time: ${env.BUILD_TIME}"

                echo("Start Deploy")
                sh "echo Deploying application for Sahid Haqqi..."
                echo("Finish Deploy")
            }
        }
    }

    post {
        always {
            echo "Job: ${env.JOB_NAME} | Build: ${env.BUILD_NUMBER} | Branch: ${env.BRANCH_NAME} | Time: ${env.BUILD_TIME}"
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
