pipeline{ 
	agent any
	stages {
		stage('build') { 
			steps {
				sh 'javac -d . scr/*.java'
				sh 'echo Main-class: Rectangulator > MANIFEST.MF'
				sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
				}
			}
		}	
	}
