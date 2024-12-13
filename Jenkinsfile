pipeline {
    agent any
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
                // Clean and package the project to generate the WAR file
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project to Tomcat...'
                // List the target directory to ensure the WAR file exists
                sh 'ls -l target/'
                
                // Copy WAR file to Tomcat's webapps directory (update path accordingly)
                sh '''
                    cp /home/xubuntu/.jenkins/workspace/edureka-jenkins.maven.assignment2/target/edureka-jenkins.maven.assignment2.war /home/xubuntu/tomcat9/webapps/
                    # Restart Tomcat to deploy the WAR file
                    sudo systemctl restart tomcat
                '''
            }
        }
    }
}
