pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://13.201.37.179:9000" -e SONAR_LOGIN="sqp_9a60924ad15ee6bdf0ba6251adfc88d25f016f1f" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms -X'
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
     
