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
			}
		}
		stage('Deploy to Development') {
			when { branch 'dev' } 
			steps {
				sh 'jenkins/deployToDev.bash'
			}
		}
		stage('Deploy to QA') {
			when { branch 'qa' } 
			steps{
				checkpoint 'Promote to QA'
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
			}
			
		}
		stage('Deploying to Production') {
			when { branch 'master' } 
			steps {
				sh 'jenkins/deployToProd.bash'
			}
			
		}
	}
}
