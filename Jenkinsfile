pipeline {
    agent any
    parameters {
        string(name: 'Integration_ID', defaultValue: '', description: 'Integration ID')
        
        string(name: 'Version', defaultValue: '01.00.0000', description: 'Integration Version')

        choice(name: 'Source_Environment', choices: ['Dev', 'Test', 'UAT', 'PROD'], description: 'Source Environment')
        
        choice(name: 'Target_Environment', choices: ['Dev', 'Test', 'UAT', 'PROD'], description: 'Target Environment')

        string(name: 'Repository_Name', defaultValue: 'oic-repository', description: 'Bucket Name')
    }
    stages {
        stage('export-integration') {
            steps {
                echo 'Export Integration..'
                build job: 'oic-export-integration', parameters: [
                    string(name: 'Integration_ID', value: "${params.Integration_ID}"),
                    string(name: 'Version', value: "${params.Version}"),
                    string(name: 'Environment', value: "${params.Source_Environment}"),
                    string(name: 'OCI_Repository', value: "${params.Repository_Name}")
                ]
            }
        }
        stage('import-integration') {
            steps {
                echo 'Import Integration..'
                build job: 'oic-import-integration', parameters: [
                    string(name: 'Integration_ID', value: "${params.Integration_ID}"),
                    string(name: 'Version', value: "${params.Version}"),
                    string(name: 'Target_Environment', value: "${params.Target_Environment}"),
                    string(name: 'Source_Environment', value: "${params.Source_Environment}"),
                    string(name: 'OCI_Repository', value: "${params.Repository_Name}")
                ]
            }
        }
    }
}
