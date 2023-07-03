pipeline {
    agent any

    stages {
        stage("Build Docker images for web-app-blogs") {
            when { changeset "web-app-blogs/*"}
                steps {
                    dir('web-app-blogs'){
                        script{
                        withCredentials([string(credentialsId: '0f1b5bc0-aed9-4215-8fe8-052c12ee790f', variable: 'nexus_ip')]) { 
                            withCredentials([usernamePassword(credentialsId: '69aab20e-345b-4e1e-a96f-17a3a5d3e2a6', passwordVariable: 'nexuspass', usernameVariable: 'nexususer')]) {
                                sh '''
                                echo ${BUILD_ID}

                                sudo docker build -t emn503/web-app-blogs:${BUILD_ID} .

                                sudo docker build -t emn503/web-app-blogs:latest .

                                sudo docker login -u $nexususer -p $nexuspass
    
                                sudo docker push emn503/web-app-blogs:${BUILD_ID}

                                sudo docker push emn503/web-app-blogs:latest

                                sudo docker rmi emn503/web-app-blogs:${BUILD_ID}
                                '''
                                }
                            }
                        }
                    }
                    
                }
        }

        stage("Build Docker images for web-app-header") {
            when { changeset "web-app-header/*"}
                steps {
                    dir('web-app-header'){
                        script{
                        withCredentials([string(credentialsId: '0f1b5bc0-aed9-4215-8fe8-052c12ee790f', variable: 'nexus_ip')]) { 
                            withCredentials([usernamePassword(credentialsId: '69aab20e-345b-4e1e-a96f-17a3a5d3e2a6', passwordVariable: 'nexuspass', usernameVariable: 'nexususer')]) {
                                sh '''
                                sudo docker build -t emn503/web-app-header:${BUILD_ID} .
                                
                                sudo docker build -t emn503/web-app-header:latest .
    
                                sudo docker login -u $nexususer -p $nexuspass
    
                                sudo docker push emn503/web-app-header:${BUILD_ID}

                                sudo docker push wemn503/eb-app-header:latest
    
                                sudo docker rmi emn503/web-app-header:${BUILD_ID}
                                '''
                                }
                            }
                        }
                    }
                    
                }
        }

        stage("Build Docker images for web-container") {
            when { changeset "web-container/*"}
                steps {
                    dir('web-container'){
                        script{
                        withCredentials([string(credentialsId: '0f1b5bc0-aed9-4215-8fe8-052c12ee790f', variable: 'nexus_ip')]) { 
                            withCredentials([usernamePassword(credentialsId: '69aab20e-345b-4e1e-a96f-17a3a5d3e2a6', passwordVariable: 'nexuspass', usernameVariable: 'nexususer')]) {
                                sh '''
                                sudo docker build -t emn503/web-container:${BUILD_ID} .

                                sudo docker build -t emn503/web-container:latest .
    
                                sudo docker login -u $nexususer -p $nexuspass
    
                                sudo docker push emn503/web-container:${BUILD_ID}

                                sudo docker push emn503/web-container:latest
    
                                sudo docker rmi emn503/web-container:${BUILD_ID}
                                '''
                                }
                            }
                        }
                    }
                    
                }
        }

    }
}