pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubcredentials', url: 'https://github.com/Selmouni-Abdelilah/aztfexport']])
                }
            }
        }
        stage('Azure login'){
            steps{
                withCredentials([azureServicePrincipal('Azure_credentials')]) {
                    sh 'az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID'
                }
            }
        }
        stage('Using Aztfexport') {
            steps {
                script { 
                    sh "mkdir -p Terraform "
                    dir("Terraform"){ 
                    sh ''' aztfexport query --overwrite --non-interactive --plain-ui "resourceGroup =~ '011-task-rg'  and (type contains 'Microsoft.Web' or type contains 'Microsoft.Logic')"'''
                    sh "terraform plan"
                }
                }
            }
        }
    }
}
