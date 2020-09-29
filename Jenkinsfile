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
                                 sudo docker.withRegistry('http://registry.hub.docker.com', 'sudo docker-hub-credentials'){
                                          image.push("${env.app_version}")      
                                
                         }
                      }
                   }
                }    
            }
                    stage('Deloy App'){
                            steps{
                               sh "doker-compose pull && docker-compose up -d"
                          
                            }        
                            
                       } 
                    
                  } 
                
            }  
