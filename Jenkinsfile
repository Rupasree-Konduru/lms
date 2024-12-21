pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://13.201.37.179:9000" -e SONAR_LOGIN="sqp_8625652be9c3251fa2994a797874f53491a16c3b" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms '
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
     
