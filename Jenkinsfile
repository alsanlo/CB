pipeline {
  agent any
  stages {
    stage('Preparación') {
      steps {
        git(url: 'https://desreposrv.goldcar.es:8443/scm/ic/checkintablet_repo.git', branch: '*/develop')
      }
    }
    stage('Ejecución') {
      steps {
        script {
          assemble
          test
        }

      }
    }
    stage('Tratamiento') {
      steps {
        archiveArtifacts 'presentation/**/*.apk'
        junit '**/TEST-*.xml'
        fingerprint 'presentation/**/*.apk'
      }
    }
  }
}