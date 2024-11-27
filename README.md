pipeline {
    agent any

    stages {
        stage('Get Dockerfile') {
            steps {
                git url: 'https://github.com/rpillaiakshay/docker-jenkins2.git', branch: 'master'
            }
        }

        stage('Create Docker Image') {
            steps {
                // Build Docker image
                sh 'echo "asd123." | sudo -S docker build -t newimage .'
            }
        }
        
        stage('Run the compose file') {
            steps {
                // Run the compose file
                sh 'echo "asd123." | sudo -S docker compose -f dockerfile.yaml up -d'
            }
        }
    }
}

