pipeline {
    agent any

    enviroment {
        VERSION = "${env.BUILD_ID}"
    }

    stages {
        stage("Build Docker images for web-app-blogs") {
            when { changeset "web-app-blogs/*"}
            steps {
                dir{}
                script{
                    withCredentials([string(credentialsId: '0f1b5bc0-aed9-4215-8fe8-052c12ee790f', variable: 'nexus_ip')]) { 
                        withCredentials([usernamePassword(credentialsId: '69aab20e-345b-4e1e-a96f-17a3a5d3e2a6', passwordVariable: 'nexuspass', usernameVariable: 'nexususer')]) {
                            sh '''
                            docker build -t $nexus_ip:8503/web-app-blogs:$VERSION .

                            docker login -u $nexususer -p $nexuspass $nexus_ip:8503

                            docker push $nexus_ip:8503/web-app-blogs:$VERSION

                            docker rmi $nexus_ip:8503/web-app-blogs:$VERSION
                            '''
                        }
                    }
                }
            }
        }

        stage("Build Docker images for web-app-header") {
            when { changeset "web-app-header/*"}
            steps {
                dir{}
                script{
                    withCredentials([string(credentialsId: '0f1b5bc0-aed9-4215-8fe8-052c12ee790f', variable: 'nexus_ip')]) { 
                        withCredentials([usernamePassword(credentialsId: '69aab20e-345b-4e1e-a96f-17a3a5d3e2a6', passwordVariable: 'nexuspass', usernameVariable: 'nexususer')]) {
                            sh '''
                            docker build -t $nexus_ip:8503/web-app-header:$VERSION .

                            docker login -u $nexususer -p $nexuspass $nexus_ip:8503

                            docker push $nexus_ip:8503/web-app-header:$VERSION

                            docker rmi $nexus_ip:8503/web-app-header:$VERSION
                            '''
                        }
                    }
                }
            }
        }

        stage("Build Docker images for web-container") {
            when { changeset "web-container/*"}
            steps {
                dir{}
                script{
                    withCredentials([string(credentialsId: '0f1b5bc0-aed9-4215-8fe8-052c12ee790f', variable: 'nexus_ip')]) { 
                        withCredentials([usernamePassword(credentialsId: '69aab20e-345b-4e1e-a96f-17a3a5d3e2a6', passwordVariable: 'nexuspass', usernameVariable: 'nexususer')]) {
                            sh '''
                            docker build -t $nexus_ip:8503/web-container:$VERSION .

                            docker login -u $nexususer -p $nexuspass $nexus_ip:8503

                            docker push $nexus_ip:8503/web-container:$VERSION

                            docker rmi $nexus_ip:8503/web-container:$VERSION
                            '''
                        }
                    }
                }
            }
        }

    }
}