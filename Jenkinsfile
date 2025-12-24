pipeline {
    agent none // Do not use a global agent so we can define them per stage

    stages {
        stage('Compile Java') {
            agent {
                docker { 
                    image 'maven:3.9.6-eclipse-temurin-17' 
                }
            }
            steps {
                echo 'Building Java Application...'
                // Compiles the Java file
                sh 'javac HelloWorld.java'
                // Optional: Run it to verify
                sh 'java HelloWorld'
            }
        }

        stage('Build Node.js') {
            agent {
                docker { 
                    image 'node:20-alphine' 
                }
            }
            steps {
                echo 'Building Node.js Application...'
                // Usually involves installing dependencies or running a build script
                sh 'node --version'
                sh 'npm install' 
                // Running a simple check for a helloworld.js
                sh 'node helloworld.js'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
