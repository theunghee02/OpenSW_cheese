node {
    def app
    stage('Clone repository') {
        git 'https://github.com/theunghee02/OpenSW_cheese.git'
    }
    stage('Build image') {
        app = docker.build("cheese/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'theunghee02') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
