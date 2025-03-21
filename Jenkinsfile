pipeline {
    agent any
    stages {
        stage("Code Clone"){
            steps{
                git url: "https://github.com/zohaibwarraich1/react-express-mysql.git", branch: "main"
                echo "Cloned Successfully!"
            }
        }
        stage("Build"){
            steps{
                sh "docker build -t react-express-mysql-frontend-image ./frontend"
                sh "docker build -t react-express-mysql-backend-image ./backend"
                echo "Build Successfully!"
            }
        }
        stage("Push on Docker-Hub"){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]){
                    sh "docker tag react-express-mysql-frontend-image:latest ${USERNAME}/react-express-mysql-frontend-image:latest"
                    sh "docker tag react-express-mysql-backend-image:latest ${USERNAME}/react-express-mysql-backend-image:latest"
                    sh "docker push ${USERNAME}/react-express-mysql-frontend-image:latest"
                    sh "docker push ${USERNAME}/react-express-mysql-backend-image:latest"
                }
                echo "Pushed Successfully!"
            }
        }
        stage("Deploy"){
            steps{
                sh "docker compose up -d"
                echo "Deployed Successfully!!"
            }
        }
    }
}
