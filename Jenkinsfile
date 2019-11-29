// define vault configuration based on your env
def configuration = [engineVersion: 1, 
                     skipSslVerification: true, 
                     timeout: 60, 
                     vaultUrl: "http://1.2.3.4:8200/", 
                     vaultCredentialId: "vault-token"]
// define vault secret path and env var
def secret = [
      [path: 'secret/jenkins', secretValues: [
        [envVar: 'ENV_USER', vaultKey: 'username'],
        [envVar: 'ENV_PASS', vaultKey: 'password']]]
]
pipeline{
    agent any
    stages{
        stage('access vault'){
            steps{
                withVault([configuration: configuration, vaultSecrets: secret]) {
                         sh '''
                         pwd
                         echo  ${ENV_USER}
                         '''
                    }
            }
        }
    }
}
