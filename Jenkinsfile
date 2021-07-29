pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'ubuntu-1804 && amd64 && docker'
    }
    stages {
        stage('build and push') {
              script {
           when {
                branch 'master'
            }
            sh("docker build -t docker/getting-started .")

            steps { 
                parallel(
                        "step 1": {  withDockerRegistry([url: "", credentialsId: "dockerbuildbot-index.docker.io"])
                    {
                    sh("docker push docker/getting-started")
                } }
                        
                )
               
            }
            
        }
    }
}
}
