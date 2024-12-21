pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://65.0.100.22:9000" -e SONAR_LOGIN="sqp_ca2bcc9845a6a1dd461864f901be502e2c09677b" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms -X'
	 }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'cd webapp && npm install && npm run build'
            }
        }  

    }
}
     
