pipeline {
    agent any
    tools {
        maven 'Maven_3.6.3'  // Ensure this matches your Maven installation name in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', url: 'https://github.com/zeeshansGitHub/edureka-jenkins.maven.assignment2.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn compile'
            }
        }
        stage('Code Review') {
            steps {
                echo 'Running Code Review...'
                // Example of a static code analysis tool like Checkstyle
                sh 'mvn checkstyle:check'
            }
        }
        stage('Unit Test') {
            steps {
                echo 'Running Unit Tests...'
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                echo 'Packaging the project...'
                sh 'mvn package'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project to Tomcat...'
                // Copy WAR file to Tomcat's webapps directory (update path accordingly)
                sh '''
                    cp target/*.war /home/xubuntu/tomcat9/webapps/
                    # Restart Tomcat to deploy the WAR file
                    sudo systemctl restart tomcat
                '''
            }
        }
    }
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
