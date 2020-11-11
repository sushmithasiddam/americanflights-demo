pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn -Dmaven.test.failure.ignore=true clean install -U -e -DskipTests'
      }
    }

    stage('Test') {
      steps {
        bat ' mvn clean -Dmaven.repo.local=C:/Users/sushmitha/.m2/repository -Dkey=mule -Denv=dev test'
      }
    }

    stage('Deploy') {
      steps {
      	withCredentials([usernamePassword(credentialsId: 'anypoint_credentials', passwordVariable: 'ANYPOINT_PASSWORD', usernameVariable: 'ANYPOINT_USERNAME')]) {
    		bat 'mvn clean -Dmaven.repo.local=C:/Users/sushmitha/.m2/repository package deploy -DmuleDeploy -DskipTests -Dkey=mule -Denv=dev -Danypoint.username=$ANYPOINT_USERNAME -Danypoint.password=$ANYPOINT_PASSWORD -Danypoint.applicationName=sample-jenkins-deployment-slsiddam'
		}
      	
        
      }
    }

  }
  tools {
    maven 'Maven'
    jdk 'JDK 8'
  }
}
