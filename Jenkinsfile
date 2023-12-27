pipeline {
agent any
stages {
    stage('NOTIFICATION-EMAIL') {
        steps {
           sh 'echo pipeline started'
      }
    }
    stage('CODE ANALYSIS-SONARQUBE') {
        steps {
           sh 'echo sonar analysis started'
            sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://http://16.171.27.152:9000" -e SONAR_LOGIN="squ_9794d56976db55a55d49d103d59cd07848b6643c"-v ".:/usr/src" sonarsource/sonar-scanner-cli
            
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
