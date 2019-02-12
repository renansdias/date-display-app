def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'node', image: 'node:carbon-jessie', command: 'cat', ttyEnabled: true)
]) {
  node(label) {
    stage('Checkout repo') {
        checkout scm
    }

    stage('Test NPM') {
        container('node') {
            sh('npm install')
            sh('npm test')
        }
    }
  }
}
