pipeline {
agent any
stages {
    stage('NOTIFICATION-EMAIL') {
        steps {
           sh 'echo pipeline started'
      }
    }
    stage('CODE ANALYSIS-SONARQUBE') {
        environment{
            SONAR_URL = "http://51.20.81.60:9000"
        }
        steps {
           withCredentials([string(credentialsId: 'sonarqube', variable: 'SONAR_AUTH_TOKEN')]) {
          sh 'cd webapp && mvn sonar:sonar -Dsonar.login=$SONAR_AUTH_TOKEN -Dsonar.host.url=${SONAR_URL}'
        }
    }
    }
    stage('BUILD FOR ARTIFACTS') {
        steps {
           sh 'echo build completed'
      }
    }
    stage('RELEASE ARTIFACTS-NEXUS') {
        steps {
           sh 'echo artifacts pushed to nexus repo'
      }
    }
    stage('BUILD IMAGES-DOCKER') {
        steps {
           sh 'echo docker images build and pushed to docker hub'
      }
    }
    stage('APPROVAL-SLACK/EMAIL') {
        steps {
           sh 'echo requsting approval to deployment'
      }
    }
    stage('DEPLOYMENT-K8S') {
        steps {
           sh 'echo application deployment completed'
      }
    }
    stage('REVERTING DEPLOYMENT') {
        steps {
           sh 'echo deployment revarted'
      }
    }
  }
}
