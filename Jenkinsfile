node('mac_for_ios') {
  scmVars = checkout scm
<<<<<<< HEAD
  grpc = "protoc-gen-objcgrpc"
  withEnv(['IROHA_PATH=iroha',
          'SCHEMA_PATH=Schema',
          'PROTOLIB_PATH=protobuf',
          'PROTO_GEN=ProtoGen',
          'LANG=en_US.UTF-8']) {
    try {
        stage('prepare') {
          sh(script: "command -v protoc >/dev/null 2>&1 || { echo 'protoc is required to continue...' >&2; exit 1; }")
          sh(script: "command -v ${grpc} >/dev/null 2>&1 || { echo 'protoc-gen-objcgrpc is required to continue...' >&2; exit 1; }")
          // err = sh(script: 'command -v protoc >/dev/null 2>&1 || { echo "protoc is required to continue..." >&2; exit 1; }', returnStatus: true)
          // err = sh(script: 'command -v $grpc >/dev/null 2>&1 || { echo "protoc-gen-objcgrpc is required to continue..." >&2; exit 1; }', returnStatus: true)
          sh(script: "git clone -b develop --depth=1 https://github.com/hyperledger/iroha")
          sh(script: "mkdir \$SCHEMA_PATH")
          sh(script: "cp -R \$IROHA_PATH/shared_model/schema \$SCHEMA_PATH/proto")
          sh(script: "rm -rf \$PROTO_GEN && mkdir \$PROTO_GEN")
        }
        stage('build') {
          sh(script: "protoc --plugin=protoc-gen-grpc=\$(command -v ${grpc}) --objc_out=\$PROTO_GEN --grpc_out=\$PROTO_GEN --proto_path=./\$SCHEMA_PATH/proto ./\$SCHEMA_PATH/proto/*.proto")
          // archiveArtifacts artifacts: 'ProtoGen/', fingerprint: true
            // sh './lib-build.sh'
        }
        checkTag = sh(script: 'git describe --tags --exact-match ${GIT_COMMIT}', returnStatus: true)
        if (scmVars.GIT_LOCAL_BRANCH ==~ /(master)/ && checkTag == 0) {
          stage('release') {
            sh(script: "pod trunk push")
          }
        }
      currentBuild.result = 'SUCCESS'
    } // end try
    catch(Exception e) {
      currentBuild.result = 'FAILURE'
    } // end catch
    finally {
      cleanWs()
    } // end finally
  }
} //end node


=======
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
>>>>>>> Fix
