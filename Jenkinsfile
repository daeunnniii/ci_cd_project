node {
    def app
    stage('Clone repository') {
        git 'https://github.com/daeunnniii/ci_cd_project.git'
    }
    stage('Build image') {
        app = docker.build("daeunnniii/prbasedtest")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
