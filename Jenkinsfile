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
                // Archieve the jar file and keep in target directory. first, go to your vm and check where the .jar file is
                archiveArtifacts 'target/hello-demo-*.jar'
            }
        }
        
        stage('Unit Test') {
            steps {
                // We use the script block to execute a groovy code within a step
                // script {
                //     for (int i = 0; i < 60; i++) {
                //         echo "${i + 1}"
                //         sleep 1
                //     }
                // }
                sh 'mvn test'
                // Whenever test are done the get saved inside target/surefire-reports
                // Archive test case report. Confirm JUit plugin is installed in jenkins
                junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
            }
            
        }
            
    }
    
}
