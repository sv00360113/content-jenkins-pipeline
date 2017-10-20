pipeline {
	agent any
		stages {
			stage('build') {
				steps {
					sh 'javac -d . src/*.java'                 
					sh 'echo Main-Class: Rectangulator > MANIFEST.MF'                 
					sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class' 
					}
			}
			stage('run') {
				steps {
					sh 'java -jar rectangle.jar 7 9' 
					}
			}
			stage('copy') {
				steps {
					sh 'cp -r /var/jenkins_home/workspace/test /tmp'
					}
			}
		}
			post { 
				success {
					archiveArtifacts artifacts: 'rectangle.jar', fingerprint: true
					}
				}
	}
