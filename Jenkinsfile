pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && docker run --rm -e SONAR_HOST_URL="http://52.66.24.136:9000" -e SONAR_LOGIN="sqp_0db48e6087585a12e93e24f497ba7d84e9a76e83" -v .:/usr/src sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms -X'
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
     
