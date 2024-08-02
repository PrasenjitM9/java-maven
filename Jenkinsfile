pipeline {
        agent { label 'master' }

	//agent any 
/*	tools {
		maven 'maven'
	}
  */  
	stages {
        
	stage('Clean') { 
            steps {
		    sh 'mvn clean' 
                    //bat 'mvn clean' 
                }
                
            }
		
	stage('Compile') { 
            steps {
                    sh 'mvn compile' 
                    //bat 'mvn compile'
                }
                
            }
/*		
	stage('Test') { 
            steps {
	          sh 'mvn test' 
                    bat 'mvn test' 
                }
                
            }
*/

	/* stage('Sonar') { 
            steps {
                withMaven(maven : 'maven'){
                    sh 'mvn sonar:sonar' 
                    bat 'mvn sonar:sonar' 
                }
                
            }
        } 
	*/
	stage('Test') { 
            steps {
                    sh 'mvn package' 
                }
                
            }

    }

    post {
        
	always {
            publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: './target/surefire-reports/', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
			
        }
    }
}
