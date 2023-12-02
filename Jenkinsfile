node {
    def app
    stage('Clone repository') {
        git 'https://github.com/theunghee02/OpenSW_cheese.git'
    }
    stage('Build image') {
        app = docker.build("theunghee02/open-sw-cheese")
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'db4d86bd-9721-45bc-9f1a-bd50bca92f4c') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
