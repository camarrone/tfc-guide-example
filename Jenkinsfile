pipeline {
  agent any
  stages {
    stage('') {
      steps {
        script {
          pipeline {
            agent any
            options {
              disableConcurrentBuilds()
            }
            stages{
              stage('Vault') {
                steps {
                  withVault(configuration: [timeout: 60, vaultCredentialId: 'Vault-Jenkins-app-role', vaultUrl: 'http://127.0.0.1:8200'], vaultSecrets: [[engineVersion: 2, path: 'secret/dev-creds/git-pass', secretValues: [[envVar: 'test', vaultKey: 'test-git-creds']]]]) {
                    sh "echo ${env.test}"
                  }
                }
              }
            }
          }
        }

      }
    }

  }
}