pipeline {
	agent {
		label 'ubuntu18_jenkins_slave01'
	}
	stages {
		stage('Build') {
			steps {
				echo 'This is BUILD stage'
				echo 'install dependencies'
				sh 'npm install'
			}
		}
		stage('Test') {
			steps {
				echo 'THis is TEST stage'
				echo 'Run test with node link'
				sh 'npm test'
			}
		}
		stage('Development') {
			when { 
				branch 'Development'
			}
			steps {
				echo 'This is DEVELOP stage'
				echo 'run test for developer check'
				sh 'npm start & sleep 5'
				echo 'address apps: http://127.0.0.1:3000'
				input message: 'Click link above to connect server and check apps for continuous or abort'
				echo 'stop server apps'
				sh 'npm stop'
			}
		}
		stage('Production') {
			when {
				branch 'Production'
			}
			steps {
				echo 'This is PRODUCT stage'
				echo 'Build product for Production stage'
			}
		}
	}
}
