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
