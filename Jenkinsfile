pipeline{
	agent any
	tools {
	    nodejs "nodejs"
	}
  stages {
	  
	  stage('Build'){

            steps{
                echo "Building..."
                sh 'npm install'
                sh 'npm start'
                }
            }
     
      stage('Test') {
          steps {
              echo 'Testing'
              sh 'npm run test'
          }
      }
  }
	post{

		always{
			echo 'Finished'
		}
		failure{
				echo 'Failure'
				emailext attachLog: true,
          body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
					to: 'laskawska.kinga@gmail.com',
					subject: "Test failed"
		}
		success{
      echo 'Success'
      emailext attachLog: true,
        body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
        to: 'laskawska.kinga@gmail.com',
        subject: "Test success"
		}
	}
}
