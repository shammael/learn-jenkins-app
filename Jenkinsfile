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
					echo "Installing dependencies... ⬇️"
					npm ci
					echo "Building... 🚀"
					npm run build
					ls -la
				'''
			}
    }

		stage("test") {
			agent {
				docker {
					image 'node:22-alpine'
					reuseNode true
				}
			}
			steps {
				sh '''
					echo "Running tests... 🧪"
					test -f build/index.html
					npm test
				'''
			}
		}
  }
}