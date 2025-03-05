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
                echo "Pushed Successfully!"
            }
        }
        stage("Deploy"){
            steps{
                echo "Deployed Successfully!"
            }
        }
    }
}
