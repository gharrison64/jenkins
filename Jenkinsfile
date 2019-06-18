pipeline{
agent none
	stages {
		stage('SCM Stage'){
			//agent {label 'mac-xamarin'}
			////environment{PATH = "/usr/local/bin:${PATH}"}
			steps{
				sh 'hostname'
				pwd()
				checkout scm
				echo 'Building...'
			//	sh 'npm -dd  install'
			//	sh 'npm -dd run build'
			}
		}
		stage('Deploy to Development'){
			when { branch 'dev' } 
			//agent{label 'ubuntu12'}
			steps{
				sh 'jenkins/deployToDev.bash'
			}
		}
		stage('Deploy to QA'){
			when { branch 'qa' } 
			//agent{label 'ubuntu12'}
			steps{
				sh 'jenkins/deployToQA.bash'
			}
			
		}
		stage('Deploy to production'){
			when { branch 'master' } 
			//agent{label 'ubuntu12'}
			steps{
				sh 'jenkins/deployToProd.bash'
			}
			
		}
	}
}
