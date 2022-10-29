node {
    stage('Continuous Download') {
    git credentialsId: 'tomcat-credentials', url: 'https://github.com/Lakshmantilak/Jenkins-practice.git'
}
stage('continuous build')
{
    sh 'mvn package'
}
stage('Continuous deployment')
{
deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://172.31.29.47:8080')], contextPath: 'qaapp', war: '**\\*.war'
}
    stage('Continuous Testing')
    {
    git 'https://github.com/Lakshmantilak/Jenkins-testing.git'
    sh 'java -jar /var/lib/jenkins/workspace/Tilak-pipeline/testing.jar'
}
stage('Continuous Delivary')
{
deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://172.31.18.99:8080')], contextPath: 'prod', war: '**\\*.war'
}
}
