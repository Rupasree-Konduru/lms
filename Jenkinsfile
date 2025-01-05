pipeline {
    agent any

    stages {
        stage('SonarAnalysis') {
            steps {
                echo 'SonarAnalysis..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://52.66.24.136:9000" -e SONAR_LOGIN="sqp_0db48e6087585a12e93e24f497ba7d84e9a76e83" -v "$(pwd):/usr/src" sonarsource/sonar-scanner-cli:5.0  -Dsonar.projectKey=lms -X'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                    cd webapp
                    npm install
                    npm run build
                '''
            }
        }
         stage('Release LMS') {
    steps {
        script {
            echo "Releasing.."       
            
            // Read the package.json and extract the version

            def packageJson = readJSON file: 'webapp/package.json'
def packageJSONVersion = packageJson.version
echo "${packageJSONVersion}"
sh "zip webapp/lms-${packageJSONVersion}.zip -r webapp/dist"
sh "curl -v -u admin:lms12345 --upload-file webapp/lms-
${packageJSONVersion}.zip http://52.66.24.136:8081/repository/lms/"
        }
        
    }
}


    }
}
