pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M398" and add it to the path.
        maven "M398"
    }

    stages {
        stage('Echo version') {
            steps {
                sh 'echo Print Maven Version'
                sh 'mvn -version'
            }
        }
        
        stage('Build') {
            steps {
                // Get some code from a GitHub repository if pasting the script directly in the pipeline
                // git 'https://github.com/InsightfulCoderDivine/jenkins-hello-world.git' // if master branch
                // git branch: 'main', url: 'https://github.com/InsightfulCoderDivine/jenkins-hello-world.git' // if main branch

                // Run Maven Package CMD
                sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Unit Test') {
            steps {
                // We use the script block to execute a groovy code within a step
                script {
                    for (int i = 0; i < 60; i++) {
                        echo "${i + 1}"
                        sleep 1
                    }
                }
                sh 'mvn test'
            }
            
        }
            
    }
    
}
