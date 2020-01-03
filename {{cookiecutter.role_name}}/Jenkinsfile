def jobnameparts = JOB_NAME.tokenize('/') as String[]
def jobconsolename = jobnameparts[0]
def branchname = jobnameparts[1]
node() {
    try {
        sh 'env'
        deleteDir()
	dir(jobconsolename){
	    stage ("Checkout scm") {
		checkout scm
	    }
	    stage ("molecule lint") {
		sh """
		molecule lint -s kvm
		"""
	    }
	    stage ("molecule create") {
		sh """
		molecule create -s kvm
		"""
	    }
	    stage ("molecule converge") {
		sh """
		molecule converge -s kvm
		"""
	    }
	    stage ("molecule idemotence") {
		sh """
		molecule idempotence -s kvm
		"""
	    }
	    stage ("molecule verify") {
		sh """
		molecule verify -s kvm
		"""
	    }
	    stage ("molecule destroy") {
		sh """
		molecule destroy -s kvm
		"""
	    }
	}
    } catch(all) {
        currentBuild.result = "FAILURE"
        throw err
    }
}
