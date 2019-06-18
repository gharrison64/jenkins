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
			steps{
				sh 'jenkins/deployToDev.bash'
			}
		}
		stage('Deploy to QA'){
			when { branch 'qa' } 
			steps{
				sh 'jenkins/deployToQA.bash'
			}
			
		}
		stage('Deploy to production'){
			when { branch 'master' } 
			steps{
				sh 'jenkins/deployToProd.bash'
			}
		}
	}
