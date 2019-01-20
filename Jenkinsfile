#! groovy

pipeline {
	agent any
	stages {
	    stage ('Build') {
	    	steps{echo 'runnig Build'}
	    }
	    stage ('Test') {
	    	steps{echo 'runnig Test'}
	    }
	    stage ('QA') {
	    	steps{echo 'runnig QA'}
	    }
	    stage ('Deploy') {
	    	steps{
		    	echo 'runnig Deploy'
		    	input('Quieres continuar?')
	    	}
	    }
	    stage ('SonarQube') {
			steps{
				sh'mvn sonar:sonar'
            }
		}

	    stage ('Execute JMeter Performance Tests'){
	     	 build job: 'jmeterFreeStyle'
	     }
	}
}
