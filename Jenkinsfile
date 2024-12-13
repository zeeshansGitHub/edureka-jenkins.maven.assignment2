pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning the repository...'
                git branch: 'main', url: 'https://github.com/zeeshansGitHub/edureka-jenkins.maven.assignment2.git'
            }
        }
        stage('Code Review') {
            steps {
                echo 'Running static code analysis...'
                sh 'mvn sonar:sonar' // Requires SonarQube configuration
            }
        }
        stage('Unit Test') {
            steps {
                echo 'Running unit tests...'
                sh 'mvn test'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project to Tomcat...'
                sh '''
                    cp /home/xubuntu/.jenkins/workspace/edureka-jenkins.maven.assignment2/target/jenkins.maven.assignment2.war /home/xubuntu/tomcat9/webapps/
                    sudo systemctl restart tomcat
                '''
            }
        }
    }
}
