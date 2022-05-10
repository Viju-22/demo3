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
        bat 'mvn package deploy -DmuleDeploy -Danypoint.userName=OssomVictory5 -Danypoint.password=Capg@1999 -Danypoint.platform.client_id=5f1c4f12e71146c1a68630eed3d2af01 -Danypoint.platform.client_secret=443B0A935Ca7428aa6d137E02FF78e56 -Denvironment=DEV'
        
        }
        }
       
   
    }
}
