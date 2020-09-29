pipeline{
        agent any
        enviroment{
            app_version= "v1"
            rollback = "false"     
                steps{
                    sh "sudo docker build -t chaperoo ."
                
                }
            stage{
                    stage("Build Image"){
                     steps{
                           script{     
                             if (env.rollback == "false"){
                                  image = docker.build("bunmi20/chaperro-frontend") 
                             }
                           
                          }
                             
                     } 
                            
               }           
                      
            stage('Tag & push Image'){
                steps{
                      scripts{
                              if (env.rollback == 'false'){
                                  docker.withRegistry('http://registry.hub.docker.com', 'docker-hun    
                                
                    sh "sudo docker run -d --name chaptodo -p 80:80 chaperoo"
                }
            }
        }    
}
