pipeline {
    agent any

    stages {
           stage('deploy to k8') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'eks-dev', contextName: '', credentialsId: 'k8-cred', namespace: 'webapp', restrictKubeConfigAccess: false, serverUrl: 'https://4D7E4783A396D839BF57AC862589C371.sk1.ap-south-1.eks.amazonaws.com') {
                  sh "kubectl apply -f deployement.yaml"// some block
                  sleep 60 // sleep for 69sec before other step run
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'eks-dev', contextName: '', credentialsId: 'k8-cred', namespace: 'webapp', restrictKubeConfigAccess: false, serverUrl: 'https://4D7E4783A396D839BF57AC862589C371.sk1.ap-south-1.eks.amazonaws.com') {
                  sh "kubectl get svc -n weapp"
                }
            }
        }
    }
}
