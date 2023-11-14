pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git branch: "main", url: 'https://github.com/dylantjl/quiz.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASPDcheck'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
