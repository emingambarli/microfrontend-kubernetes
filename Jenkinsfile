pipeline {
    agent any

    stages {
        stage("Build Docker images for web-app-blogs") {
            when { changeset "web-app-blogs/*"}
                steps {
                    dir('web-app-blogs'){
                        script{
                            withCredentials([usernamePassword(credentialsId: 'a4b0f15b-5736-4f66-998d-238687ce3d99', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                                sh '''
                                echo ${BUILD_ID}

                                sudo docker build -t emn503/web-app-blogs:${BUILD_ID} .

                                sudo docker build -t emn503/web-app-blogs:latest .

                                sudo docker login -u $dockeruser -p $dockerpass
    
                                sudo docker push emn503/web-app-blogs:${BUILD_ID}

                                sudo docker push emn503/web-app-blogs:latest

                                sudo docker rmi emn503/web-app-blogs:${BUILD_ID}
                                '''
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
                            withCredentials([usernamePassword(credentialsId: 'a4b0f15b-5736-4f66-998d-238687ce3d99', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                                sh '''
                                sudo docker build -t emn503/web-app-header:${BUILD_ID} .
                                
                                sudo docker build -t emn503/web-app-header:latest .
    
                                sudo docker login -u $dockeruser -p $dockerpass
    
                                sudo docker push emn503/web-app-header:${BUILD_ID}

                                sudo docker push emn503/web-app-header:latest
    
                                sudo docker rmi emn503/web-app-header:${BUILD_ID}
                                '''
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
                            withCredentials([usernamePassword(credentialsId: 'a4b0f15b-5736-4f66-998d-238687ce3d99', passwordVariable: 'dockerpass', usernameVariable: 'dockeruser')]) {
                                sh '''
                                sudo docker build -t emn503/web-container:${BUILD_ID} .

                                sudo docker build -t emn503/web-container:latest .
    
                                sudo docker login -u $dockeruser -p $dockerpass
    
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