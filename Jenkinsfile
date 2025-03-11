  pipeline {
    agent any

    stages {
        stage('Debug Variables') {
            steps {
                script {
                    println "WORKSPACE: ${env.WORKSPACE}"
                }
            }
        }
        stage('Hello') {
            steps {
                bat ''' 
                npm --version
                dir
                '''
            }
        }
        stage('Docker Hello') {
            agent {
                
                docker {
                    image 'node'
                    reuseNode true
                    args '-v  cd c:/programdata/jenkins/.jenkins/workspace\testtool:/workspace -w /workspace'
                    
                }
            }
            steps {
                
                script {
                    
                    def imageName = 'node:10'.toLowerCase()

                    // Use the correct image name
                    docker.image(imageName).inside {
                        bat "Running Docker'node:10'r with node:10 image"
                    }
                }
            }
        }
    }
    
}
