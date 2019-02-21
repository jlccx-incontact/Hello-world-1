#!groovy​

import org.jenkinsci.plugins.workflow.steps.FlowInterruptedException
def CUSTOM_VERSION
def ARTIFACT_FILENAME
def customContainer

def destroyInfrastructure = false
def didTimeout = false

// Parameter used to recover the JFROG_ARTIFACTORY_BUILD_USER credential username only
def JFROG_ARTIFACTORY_BUILD_USERNAME
// Parameter used to recover the JFROG_ARTIFACTORY_BUILD_USER api key value only
def JFROG_ARTIFACTORY_BUILD_USER_API_KEY
// Artifactory url used for any other branch except master.
def JFROG_ANY_SERVER_URL="http://incontact-docker-snapshot-local.jfrog.io"
// Artifactory url used only for the master branch.
def JFROG_MASTER_SERVER_URL="http://incontact-docker-release-local.jfrog.io"
// We are setting the JFROG_SERVER_URL initial value by default.
def JFROG_SERVER_URL = "${JFROG_ANY_SERVER_URL}"

//Parameter used for the container image URL
def JFROG_IMAGE_URL
//Parameter used for constructing the container image URL
def JFROG_SERVER_HOST = "incontact-docker-snapshot-local.jfrog.io"

def JFROG_ARTIFACTORY_BUILD_CREDENTIAL = "artifactoryBuildUser1"

def isMasterBranch = false
def manualGate

// Workaround for the issue
// groovy.lang.MissingPropertyException: No such property: myCustomProperty for class: WorkflowScript
// Is recommended to use this fix for parameters that have a constant value only
def bucketStateFolder = null
if (env.bucketStateFolder) {
  	bucketStateFolder = env.bucketStateFolder
} else {
	// Set the default value for the parameter bucketStateFolder here
	// Please be sure that the bucket name used is valid.
	// You can take a look the site: https://docs.aws.amazon.com/AmazonS3/latest/dev/BucketRestrictions.html
  	bucketStateFolder = "xyz-sfdc-sfomnirouter-state2-abc"
  	env.bucketStateFolder = bucketStateFolder
}
echo "The parameter bucketStateFolder has the next value: ${bucketStateFolder}"


if (env.JFROG_SERVER_URL) {
  JFROG_SERVER_URL = env.JFROG_SERVER_URL
} else {
  JFROG_SERVER_URL = "${JFROG_ANY_SERVER_URL}"
  env.JFROG_SERVER_URL = "${JFROG_ANY_SERVER_URL}"
}

def jfrogImageUrl

// All the Dockerfile images used on this pipeline belong to the repository 
// https://github.com/inContact/cicd-concourse-docker/tree/master/docker/cicd/toolbox


pipeline {

  agent none

  options {
    buildDiscarder logRotator( daysToKeepStr: '8', numToKeepStr: '5') 
  }

  environment {
      MY_VAR"Hello Worldx!!!"
	}


  stages {

	stage('Build') {
    	steps {
    		script {
          		node {
                  println "\n${MY_VAR}\n"
          		}
        	}
    	}
  }



  } // stages closed

}

