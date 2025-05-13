pipeline {
    agent any
    
    environment {
        SONAR_TOKEN = credentials('SONAR_TOKEN')  // Refers to the token stored in Jenkins Credentials
    }

    stages {
        stage('SonarCloud Analysis') {
            steps {
                script {
                    // Download SonarScanner CLI
                    sh ''' 
                    curl -sSLo sonar-scanner-cli.zip https://github.com/SonarSource/sonar-scanner-cli/releases/download/4.7.0.2747/sonar-scanner-cli-4.7.0.2747-linux.zip
                    unzip sonar-scanner-cli.zip
                    export PATH=$PATH:$(pwd)/sonar-scanner-4.7.0.2747-linux/bin
                    '''
                    
                    // Run the SonarScanner command
                    sh ''' 
                    ./sonar-scanner -Dsonar.projectKey=namitjain123_8.2CdevSecOps \
                        -Dsonar.organization=namitjain123 \
                        -Dsonar.host.url=https://sonarcloud.io \
                        -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }
    }
}
