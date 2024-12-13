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
                sh 'mvn package'  // This will generate the .war file in the target directory
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project to Tomcat...'
                // Copy WAR file to Tomcat's webapps directory (update path accordingly)
                sh '''
                    cp target/edureka-jenkins.maven.assignment2.war /home/xubuntu/tomcat9/webapps/
                    # Restart Tomcat to deploy the WAR file
                    sudo systemctl restart tomcat
                '''
            }
        }
    }
}
