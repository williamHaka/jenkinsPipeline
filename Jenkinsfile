#!groovy
pipeline {
	agent any
	stages {
		stage ('Compilar') {
			steps{
				echo 'Verificar proyecto'
				bat 'mvn compile'
	    	}
		}
		stage (Test) {	
			steps{
				echo 'Compilando proyecto'
//				bat 'mvn test'
			}
		}
		stage ('Intalar') {
			steps{
				echo 'Iniciando Test'
				//bat 'mvn install'
			}
		}
	}
}
