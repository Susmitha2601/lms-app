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
            sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://http://16.171.27.152:9000" -e SONAR_LOGIN="sqp_c5f20de1ee1a200f2ee80696df86e5b599e74658"-v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey="lms"
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
