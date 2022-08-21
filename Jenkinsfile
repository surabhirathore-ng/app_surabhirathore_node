pipeline{
    agent any
	    tools
		{
		nodejs "nodejs"
			
		}
		
		environment {
		scannerHome = tool name: 'sonar_scanner_dotnet'
		username = 'admin'
		appName = 'SampleApp'
		}
	
    stages{
        stage('Checkout'){
        steps{
            echo "build in master branch -1"
			checkout scm
        }
		}
		
		stage('Build'){
        steps{
            echo "build in master branch -2"
			 sh 'npm install'
        }
		}
		
		
		stage('Sonar Analysis'){
        steps{
		    echo "sonar analysis in master branch -4"
			withSonarQubeEnv("Test_Sonar")
			{
			 sh "npm sonar:sonar"
			}
        }
		}
				
		
		stage('Docker Image'){
        steps{
		    echo "Docker Image in master branch -6"
			sh "docker build -t helloworld:v1 --no-cache -f Dockerfile ."
			}
        }
		
		stage('Push to DTR'){
        steps{
		    echo "Push to DTR in master branch -7"
			sh "docker push surabhirathore/buildimagerepo"
        }
		}
		
		
		}
		
		
    }