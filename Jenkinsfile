@Library("Shared") _
pipeline{
    agent { label "vinod"}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
              script{
                clone("https://github.com/jaypandya594/react_django_demo_app", "main" )
              }
            }
        }
        stage("Build"){
            steps{
                script{
                    // FIXED: Order is now (ProjectName, ImageTag, DockerHubUser)
                    docker_build("demo_app", "latest", "jaypandya1234")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
               script{
                  // FIXED: Order is now (ProjectName, ImageTag, DockerHubUser)
                  docker_push("demo_app", "latest", "jaypandya1234")   
               }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                // Ensure docker-compose.yml is in the root of your repo
                sh " docker compose up -d"
            }
        }
    }
}
