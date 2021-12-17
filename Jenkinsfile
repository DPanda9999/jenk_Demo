pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
           echo "build success"
      }
    }
    stage('Test') {
      steps {
          echo "mvn test starts"
      }
    }
    stage('Deploy Development') {
      steps {
			- MUNITCOVER="$(grep -m1 "<runCoverage>" pom.xml | awk -F ">" '{print $2}' | awk -F "<" '{print $1}')"
            - MUNITBUILD="$(grep -m1 "<failBuild>" pom.xml | awk -F ">" '{print $2}' | awk -F "<" '{print $1}')"
            - MUNITREQ="$(grep -m1 "<requiredApplicationCoverage>" pom.xml | awk -F ">" '{print $2}' | awk -F "<" '{print $1}')"
            - echo $MUNITCOVER
            - echo $MUNITBUILD
            - echo $MUNITREQ
            - if [ "$MUNITCOVER" = "true" ] && [ "$MUNITBUILD" = "true" ] && [ "$MUNITREQ" -ge "1" ];then
            - echo "MUNIT is enabled"
            - else echo "MUNIT is not enabled in pom.xml recopy the pom.xml from the default_mulesoft_templates repo"; set -e; exit 1;
            - fi
            bat "mvn clean package deploy -DmuleVersion=4.4.0 -Dusername=rishikasuri2701 -Dpassword=Comicoctober@21 -DapplicationName=jenk-sample -Denvironment=Sandbox -Dworkers=1 -DworkerType=Micro -DmuleDeploy"
            echo "deploy success"
	  }
	}
  }
}