node {
    def mvnHome = tool 'maven-3.5.2'
    def dockerImageTag = "devopsexample:${env.BUILD_NUMBER}"
    
    stage('Clone Repo') {
        git 'https://github.com/vikas4cloud/DevOps-Example.git'
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
        sh "docker login -u jatinkapoor009 -p Muskan@5252"
    }
    
    stage('Docker Push') {
        sh "docker tag ${dockerImageTag} jatinkapoor009/myapplication:${env.BUILD_NUMBER}"
        sh "docker push jatinkapoor009/myapplication:${env.BUILD_NUMBER}"
    }
}
