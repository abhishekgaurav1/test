node("docker") {
    docker.withRegistry('abhishekgaurav/test', 'dockercreds') {
    
        git url: "https://github.com/abhishekgaurav1/javaee7-simple-sample.git", credentialsId: 'githubcreds'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
