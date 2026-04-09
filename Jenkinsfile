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
}
