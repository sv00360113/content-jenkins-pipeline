pipeline {
	agent any 
		stages {
			stage('install') {
					steps { 
						sh 'sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo'
						sh 'sudo yum clean all'
						sh 'yum-config-manager --disable download'
						sh 'sudo yum install docker'
						sh 'sudo service docker start'
						}
					}
                       stage('test') {
				steps {
					sh 'sudo docker pull tomcat'
					sh 'sudo docker images'
					}
			}
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
					sh 'cp -r /var/jenkins_home/workspace/test/rectangle.jar /tmp'
					}
			}
		}
			post { 
				success {
					archiveArtifacts artifacts: 'rectangle.jar', fingerprint: true
					}
				}
	}
