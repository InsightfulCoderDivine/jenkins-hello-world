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
                // Get some code from a GitHub repository
                // git 'https://github.com/InsightfulCoderDivine/jenkins-hello-world.git' // if master branch
                git branch: 'main', url: 'https://github.com/InsightfulCoderDivine/jenkins-hello-world.git' // if main branch

                // Run Maven Package CMD
                sh "mvn clean package -DskipTests=true"
            }
        }
        
        stage('Unit Test') {
            steps {
                sh 'mvn test'
            }
            
        }
            
    }
    
}
