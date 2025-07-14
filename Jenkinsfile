node {
    def mvnHome = tool 'maven-3.5.2'
    def dockerImageTag = "jatinimage:${env.BUILD_NUMBER}"
    
    stage('Clone Repo') {
        git 'https://github.com/jatinkapoor009/cicd_repo.git'
    }    
    
    stage('Build Project') {
        sh "'${mvnHome}/bin/mvn' clean install"
    }
    
    stage('Build Docker Image') {
        dockerImage = docker.build(dockerImageTag)
    }
    
    stage('Docker Login') {
        echo "Docker Image Tag Name: ${dockerImageTag}"
        sh "docker images"
        sh "docker login -u jatink9599 -p jatink9599@gmail.com"
    }
    
    stage('Docker Push') {
        sh "docker tag ${dockerImageTag} jatink9599/myapplication:${env.BUILD_NUMBER}"
        sh "docker push jatink9599/myapplication:${env.BUILD_NUMBER}"
    }
}
