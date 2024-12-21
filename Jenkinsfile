pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://3.110.194.220:9000" -e SONAR_LOGIN="sqp_ebe6f491756a4a3e9f916a35f8500ea5581290b8" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=LMS'
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
     
