environment {
    registry = "jaels/"
    registryCredential = 'dockerhub'
}

podTemplate(label: 'mypod', containers: [
    containerTemplate(name: 'docker', image: 'docker:stable', command: 'cat', ttyEnabled: true)
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
  ]
  ) {
    node('mypod') {
        checkout scm
        stage('Check running containers') {
            container('docker') {
                sh 'ls -l'
                sh 'docker build -t web_nginx .'
            }
        }
    }
}
