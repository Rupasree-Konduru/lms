pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://54.187.86.13:9000" -e SONAR_LOGIN="sqp_9199cfcc68203bf38205b03a2571ca1dd641809c" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
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
     
