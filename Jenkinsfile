environment {
    registry = "jaels/nginx-php"
    registryCredential = ‘dockerhub’
    dockerImage = ''
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
        stage('build nginx') {
            container('docker') {
                sh 'echo $registry'
                //sh 'docker build -t "$registry" nginx'
            }
        }
    }
}
