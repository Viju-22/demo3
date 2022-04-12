pipeline
{
    agent any
	
	environment{
		
		env_dev='DEV'
	}
	
    
    stages{
        stage('Build Application'){
        steps{
        bat 'mvn clean install'
        }
      
        }
        
        stage('SonarQube Testing'){
        steps{
        bat 'mvn sonar:sonar -Dsonar.sources=src/ -Dsonar.host.url=http://localhost:9000 -Dsonar.login=c91a76d35e003f1d1af99856195a65522c327514'
            }
        }
       
        stage('Deploy Application To Mulesoft '){
		
	when {
                branch 'dev'
            }
		
        steps{	
        bat 'mvn package deploy -DmuleDeploy -Danypoint.userName=OssomVictory4 -Danypoint.password=Capg@1999 -Danypoint.platform.client_id=8a63220dbc214eb8b77eddea431b6dc7 -Danypoint.platform.client_secret=14A67deF702C4136A591c88E7A49ac7b -Denvironment=${env_dev}'
        
        }
        }
       
   
    }
}
