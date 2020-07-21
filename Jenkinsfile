pipeline {
	agent any
	stages {
		stage('Lint HTML') {
			steps {
				sh 'tidy -q -e *.html'
				}
			}
		stage('Upload to AWS') {
			steps {
				withAWS(region:'us-west-2',credentials:'aws-static') {
                  		sh 'echo "Uploading the file from github to s3"'
                      			s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacity-jenkins-aws')
				}
			}
		}
	}
}
