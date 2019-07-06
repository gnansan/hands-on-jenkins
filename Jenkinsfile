pipeline {
  agent any
  stages {
    
    
  	def myRepo = checkout scm
	def gitCommit = myRepo.GIT_COMMIT
	def gitBranch = myRepo.GIT_BRANCH
	def shortGitCommit = "${gitCommit[0..10]}"
	def previousGitCommit = sh(script: "git rev-parse ${gitCommit}~", returnStdout: true)

    stage('Build') {
      steps {
        echo 'Building...'
      }
    }
    stage('Test') {
      parallel {
        stage('Test Firefox') {
          steps {
            sh 'echo \'Testing Firefox\''
          }
        }
        stage('Test Chrome') {
          steps {
            sh 'echo \'Testing Chrome\'; exit 1'
          }
        }
        stage('Test Edge') {
          steps {
            sh 'echo \'Testing Edge\''
          }
        }
      }
    }
    stage('testing github branch') {

	         // fetching from SCM:
            echo "$myRepo.GIT_BRANCH"
            echo gitBranch
            echo "$gitBranch"
        	git branch: 'video53',
          url: 'https://github.com/gnansan/hands-on-jenkins.git',
          sh 'ls -lath'
 
	    
	    steps {
        echo 'Deploy'
      }
    }
  }
}
