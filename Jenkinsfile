pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'gradle javadoc'
      }
    }
    stage('Mail-Notification') {
      steps {
        mail(subject: 'Jenkins Notification TP_Outils', body: 'Un nouveau push dans le repo TP_Outils', to: 'fc_harouit@esi.dz ; fa_bouchebaba@esi.dz')
      }
    }
    stage('Code Check') {
      parallel {
        stage('Test Reporting') {
          steps {
            sh 'gradle jacoco'
          }
        }
        stage('Code Analysis') {
          steps {
            sh 'echo "sonar"'
          }
        }
      }
    }
  }
}