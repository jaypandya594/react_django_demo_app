@Library("Shared") _
pipeline{
    
    agent {label "vinod"}
    
    stages{
         
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/jaypandya594/react_django_demo_app.git", "main")
                }
            }
        }
        
        stage("Build"){
            steps{
                script{
                    docker_build("react-notes-app","latest","jaypandya1234")
                }
            }
        }
        stage("push to DockerHub"){
            steps{
                script{
                    docker_push("react-notes-app", "latest", "jaypandya1234")
                }
            }
        }
        
        stage("Test"){
            steps{
               echo "This is testing the code"
              
            }
        }
        
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d "
            }
            
        }
    }
}
