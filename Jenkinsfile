#! groovy

pipeline {
	agent any
	stages {
	    stage ('Compilar') {
	    	steps{
		    	echo 'compilando aplicacion'
		    	bat 'mvn compile'
		    	echo 'compilación Exitosa'
	    	}
	    }
	    stage ('Test') {
	    	steps{
    			echo 'Ejecutando tests'
//	    		try{
			      bat 'mvn clean install'
//			      step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
//			   }catch(err) {
//			      step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
//			      if (currentBuild.result == 'UNSTABLE')
//			         currentBuild.result = 'FAILURE'
//			      throw err
//			   }
	    	}
	    }
	    stage ('Instalar') {
	    	steps{
	    		echo 'Instala el paquete generado en el repositorio maven'
   				bat 'mvn install -Dmaven.test.skip=true'
    		}
	    }
	    stage ('Archivar') {
	    	steps{
		    	echo 'Archiva el paquete el paquete generado en Jenkins'
   				step([$class: 'ArtifactArchiver', artifacts: '**/target/*.jar, **/target/*.war', fingerprint: true])
//		    	input('Quieres continuar?')
	    	}
	    }
	    
	    //stage ('SonarQube') {
		//	steps{
		//		sh'mvn sonar:sonar'
        //    }
		//}
		
	    stage ('Execute JMeter Performance Tests'){
	    	steps{
	    	echo 'ejecuta prueba de carga'
	     	 	build 'jmeterFreeStyle'
     	 	}
	     }
	}
}
