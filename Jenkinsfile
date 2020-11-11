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
        bat 'mvn clean -Dmaven.repo.local=C:/Users/sushmitha/.m2/repository package deploy -DmuleDeploy -DskipTests -Dkey=mule -Denv=dev'
      }
    }

  }
  tools {
    maven 'Maven'
    jdk 'JDK 8'
  }
}
