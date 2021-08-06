pipeline{
        agent any
        stages{
            stage('Clone Repo'){
                steps{
                    sh "git fetch https://gitlab.com/qacdevops/chaperootodo_client.git"
                }
            }
            stage('Install Docker + Docker Compose'){
                steps{
                    sh 'curl https://get.docker.com | sudo bash'
                    sh 'sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose'
                    sh 'sudo chmod +x /usr/local/bin/docker-compose'
                }
            }
            stage('Deploy Application'){
                steps{
                    sh 'sudo docker-compose pull && sudo -E DB_PASSWORD="testpassword"'
                    sh 'docker-compose up -d'
                }
            }
        }
}
