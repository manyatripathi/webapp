node 
{
  def MAVEN_HOME = tool name: 'MAVEN_HOME', type: 'maven'
      def JAVA_HOME = tool "JAVA_HOME"
      env.PATH="${env.PATH}:${MAVEN_HOME}/bin:${JAVA_HOME}/bin"
  stage('code checkout')
  {
      git 'https://github.com/manyatripathi/my-app'
  }
  stage('compile-package')
  {
      sh "sudo mvn clean"
      sh "sudo mvn compile"
      sh "sudo mvn package"
  }
  stage('SOnarQube Analysis')
  {
      withSonarQubeEnv('sonar-1')
      {
          sh 'sudo mvn sonar:sonar -Dsonar.host.url="http://localhost:9000"'
      }
  }
}
