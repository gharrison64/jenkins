pipeline {
agent any
	stages {
		stage('SCM Stage'){
			steps{
				sh 'hostname'
				pwd()
				checkout scm
				echo 'Building...'
			}
		}
		stage('Deploy to Development'){
			when { branch 'dev' } 
			agent{label 'ubuntu12'}
			steps{
				sh 'jenkins/deployToDev.bash'
				}
		}
		stage('Deploy to QA Approval'){
			when { branch 'qa' } 
			steps{
				checkpoint 'Approve QA Deployment'
			}
		}
		stage('Deploy to QA'){
			when { branch 'qa' } 
			agent{label 'ubuntu12'}
			steps{
				sh 'jenkins/deployToQA.bash'
			}
			
		}
		stage('Deploy to Production Approval'){
			when { branch 'master' } 
			steps{
				checkpoint 'Approve Production Deployment'
			}
		}
		stage('Deploy to production'){
			when { branch 'master' } 
			agent{label 'ubuntu12'}
			steps{
				sh 'jenkins/deployToProd.bash'
			}
			
		}
	}
}
