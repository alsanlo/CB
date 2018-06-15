pipeline {
  agent any
  stages {
    stage('Preparacion') {
      steps {
        git(url: 'https://desreposrv.goldcar.es:8443/scm/ic/checkintablet_repo.git', branch: '*/develop')
        withCredentials(bindings: [string(credentialsId: 'KeyStorePassword', variable: 'KSTOREPWD')])
        withCredentials(bindings: [string(credentialsId: 'KeyPassword', variable: 'KEYPWD')])
      }
    }
    stage('Ejecucion') {
      steps {
        script {
          assemble
          test
        }

        sh '''gradle assemble
gradle test'''
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