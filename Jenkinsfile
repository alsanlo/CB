pipeline {
  agent any
  stages {
    stage('Preparaci�n') {
      steps {
        git(url: 'https://desreposrv.goldcar.es:8443/scm/ic/checkintablet_repo.git', branch: '*/develop')
      }
    }
    stage('Ejecuci�n') {
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