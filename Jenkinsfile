env.SCM_URL="https://github.com/diannaowa/cicd.git"
env.BRANCH_NAME="master"
//env.REPO_RELEASE="https://registry.hub.docker.com"
env.REPO_RELEASE="https://192.168.33.31:8000"
env.BUILD_VERSION="1.3"
env.REPO_CREDENTIALS="nexus"
node{
    stage "checkout"
        git  url: "${env.SCM_URL}", branch: "${env.BRANCH_NAME}"
    stage "build"
        def dockerImage = docker.build("duizhang/app:1.0")
        docker.withRegistry("${env.REPO_RELEASE}","${env.REPO_CREDENTIALS}") {
            dockerImage.push("${env.BUILD_VERSION}")
           // dockerImage.push("latest")
        }
   
}
