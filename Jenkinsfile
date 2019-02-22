node('mac_for_ios') {
  scmVars = checkout scm
  try {
      stage('build') {
          sh './lib-build.sh'
      }
    currentBuild.result = 'SUCCESS'
  } // end try
  catch(Exception e) {
    currentBuild.result = 'FAILURE'
  } // end catch
  finally {
    cleanWs()
  } // end finally
} //end node
