node('master') {
    printMessage("Pipeline Start")

    stage("Fetch Source Code") {
	cleanWs()
        git([url: 'https://github.com/RahulGandhi11/Lesson5', branch: 'add-functions-and-tests'])
    }

    dir('.') {
	printMessage('Running Pipeline')
        stage("Testing") {
            sh 'ls -la'
	    sh 'python test_functions.py'
        }
        stage("Deployment") {
            if (env.BRANCH_NAME == 'master') {
		printMessage('Deploying the master branch')
	    } else {
		printMessage("No deployment for branch [${env.BRANCH_NAME}]")
	    }
        }
    printMessage("Pipeline End")
  }
}

def printMessage(message) {
    echo "${message}"
}
