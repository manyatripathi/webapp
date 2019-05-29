node 
{
  def MAVEN_HOME = tool name: 'MAVEN_HOME', type: 'maven'
      def JAVA_HOME = tool "JAVA_HOME"
      env.PATH="${env.PATH}:${MAVEN_HOME}/bin:${JAVA_HOME}/bin"
  stage('code checkout')
  {
      git 'https://github.com/manyatripathi/webapp'
  }
  stage('compile-package')
  {
      sh "mvn clean"
      sh "mvn compile"
      sh "mvn package"
  }
  stage('SOnarQube Analysis')
  {
      withSonarQubeEnv('sonar-1')
      {
          sh 'mvn sonar:sonar -Dsonar.host.url="http://localhost:9000"'
      }
  }
}
