pipeline {
	agent any
	stages {
		stage('SCM Stage') {
			steps {
				sh 'hostname'
				pwd()
				checkout scm
				echo 'Building...'
			}
		}
		stage('Deploy to Development') {
			when { branch 'dev' } 
			steps {
				checkpoint 'Promote to Dev'
				sh 'jenkins/deployToDev.bash'
			}
		}
		stage('Deploy to QA') {
			when { branch 'qa' } 
			steps{
				checkpoint 'Promote to QA'
				sh 'jenkins/deployToQA.bash'
			}
			
		}
		stage('Deploying to Production') {
			when { branch 'master' } 
			steps {
				checkpoint 'Promote to Production'
				sh 'jenkins/deployToProd.bash'
			}
			
		}
	}
}
