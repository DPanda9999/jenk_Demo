pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
           echo "build success"
      }
    }
    stage('Unit Test') { 
      steps {
        sh 'mvn clean test'
      }
    }
    stage('Test') {
      steps {
          echo "mvn test starts"
      }
    }
    stage('Deploy Development') {
      steps {
            bat "mvn clean package deploy -DmuleVersion=4.4.0 -Dusername=rishikasuri2701 -Dpassword=Comicoctober@21 -DapplicationName=jenk-sample -Denvironment=Sandbox -Dworkers=1 -DworkerType=Micro -DmuleDeploy"
            echo "deploy success"
	  }
	}
  }
}