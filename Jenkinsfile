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
				sh 'jenkins/deployToDev.bash'
			}
		}
		stage ('Deploy to QA Checkpoint'){
			steps{
				checkpoint 'Promote to QA'
				echo 'Promoting...'
			}
		}
		stage('Deploy to QA') {
			when { branch 'qa' } 
			steps{
				sh 'jenkins/deployToQA.bash'
			}
			
		}
		stage ('Deploy to Production Checkpoint'){
			steps{
				checkpoint 'Promote to Production'
				echo 'Promoting...'
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
