pipeline{
    agent any
    stages{
        stage("docker_image"){
            steps{
                sh "docker build -t cicd ."
            }
        }
        stage("dev_docker_rm_and_new"){
            steps{
                sh 'docker stop cicd && docker rm cicd'
		}
        }
        stage("deploy"){
            steps{
                echo "container port is 8081"
		sh 'docker run -it -d --restart unless-stopped --name=cicd -p 8081:80 cicd' 
		sh 'docker image prune -f'
            }
        }

    }
}
