pipeline {
    agent any

    stages {
        
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://34.212.183.76:9000" -e SONAR_LOGIN="sqp_9199cfcc68203bf38205b03a2571ca1dd641809c" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
	 }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'cd webapp && npm install && npm run build'
            }
        }  
         stage('Release LMS') {
            steps {
                script {
                    echo "Releasing.."       
                    def packageJSON = readJSON file: 'webapp/package.json'
                    def packageJSONVersion = packageJSON.version
                    echo "${packageJSONVersion}"  
		    sh "sudo dnf install zip"
                    sh "zip webapp/dist-${packageJSONVersion}.zip -r webapp/dist"
                    sh "curl -v -u admin:Kmshdr@12345 --upload-file webapp/dist-${packageJSONVersion}.zip http://34.212.183.76:8081/repository/lms/"     
            }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    echo "Deploying.."       
                    }
		}
	}
	}
	}
     
