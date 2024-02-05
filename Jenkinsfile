pipeline {
    agent any

       stages {
        stage('Sonar Analysis') {
            steps {
                echo 'Analyze Code..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://34.212.183.76:9000" -e SONAR_LOGIN="sqp_9199cfcc68203bf38205b03a2571ca1dd641809c" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
            }
        }
	}I		
        stage('Building') {
            steps {
                echo 'Build Code..'
		sh 'cd webapp && npm install && npm run build'
	}
      }
	
       }
     
