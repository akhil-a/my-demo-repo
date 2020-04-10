pipeline {
   agent { node { label 'wfh' } }

   stages {
      stage('Hello') {
         steps {
            echo 'Hello World'
         }
      }
   }
   node('wfh') {
    checkout scm
    def app
    app = docker.build("akhilanil10/test_alpine1")
   }
}

