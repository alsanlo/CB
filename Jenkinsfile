pipeline {
  agent any
  stages {
    stage('Preparación') {
      steps {
        git(url: 'https://desreposrv.goldcar.es:8443/scm/ic/checkintablet_repo.git', branch: '*/develop')
        withCredentials([string(credentialsId: 'KeyStorePassword', variable: 'KSTOREPWD')])
        {
          //Acciones a realizar con credenciales
        }
        withCredentials([string(credentialsId: 'KeyPassword', variable: 'KEYPWD')])
        {
          //Acciones a realizar con credenciales
        }
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
