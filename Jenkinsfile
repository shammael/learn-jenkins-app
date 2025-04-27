pipeline {
  agent any
  stages {
    stage("Build")
    {
			agent {
				docker {
					image 'node:22-alpine'
					reuseNode true
				}
			}
      steps {
				sh '''
					ls -la
					npm --version
					node --version
					echo "Installing dependencies... ⬇️"
					npm ci
					echo "Building... 🚀"
					npm run build
					ls -la
				'''
			}
    }
  }
}