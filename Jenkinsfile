pipeline {
    agent any
    
    environment {
        KEPTN_ENDPOINT = 'http://10.5.10.11:80/api'
        KEPTN_API_TOKEN = 'GQKW4Zgt4YfnGjhkGxKW65sosZkj13MktN14eeErRi9Zh'
        KEPTN_PROJECT = 'dynatrace'
        KEPTN_SERVICE = 'autser'
        KEPTN_STAGE = 'quality-gate'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        //stage('Build') {
            //steps {
                // Perform your build steps here
            //}
        //}
        
        //stage('Test') {
            //steps {
                // Perform your test steps here
            //}
        //}
        
        stage('Deploy') {
            steps {
                script {
                    def keptn = [:]
                    keptn['endpoint'] = env.KEPTN_ENDPOINT
                    keptn['apiToken'] = env.KEPTN_API_TOKEN
                    keptn['project'] = env.KEPTN_PROJECT
                    keptn['service'] = env.KEPTN_SERVICE
                    keptn['stage'] = env.KEPTN_STAGE
                    
                    sh """
                    keptn configure --endpoint=${keptn.endpoint} --api-token=${keptn.apiToken}
                    keptn trigger delivery --project=${keptn.project} --service=${keptn.service} --stage=${keptn.stage} --sequence=your-deployment-sequence
                    """
                }
            }
        }
    }
}
