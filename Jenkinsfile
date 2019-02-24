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
                sh 'ls -l'
                sh 'docker build jaels/nginx-php:latest -f site/Dockerfile'
            }
        }
    }
}
