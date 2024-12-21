pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://13.201.37.179:9000" -e SONAR_LOGIN="squ_4e857d95bbba46ef506a2f6a7da053cced9008b3" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms -X'
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
     
