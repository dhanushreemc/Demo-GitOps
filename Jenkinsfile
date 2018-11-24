void setBuildStatus(String message, String state) {
  step([
      $class: "GitHubCommitStatusSetter",
      reposSource: [$class: "ManuallyEnteredRepositorySource", url: "https://github.com/dhanushreemc/Demo-GitOps.git"],
      contextSource: [$class: "ManuallyEnteredCommitContextSource", context: "ci/jenkins/build-status"],
      errorHandlers: [[$class: "ChangingBuildStatusErrorHandler", result: "UNSTABLE"]],
      statusResultSource: [ $class: "ConditionalStatusResultSource", results: [[$class: "AnyBuildResult", message: message, state: state]] ]
  ]);
}
pipeline {
    agent any
    stages {
         stage("checkout"){
             steps {
                checkout scm
             }
         }
         stage("result") {
             steps {
                 echo "Build successful"
             }
         }
     }
     post {
        success {
              setBuildStatus("Build succeeded", "SUCCESS");
        }
        failure {
              setBuildStatus("Build failed", "FAILURE");
        }
     }
}
