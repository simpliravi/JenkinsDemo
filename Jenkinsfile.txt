node{
   def mvnHome
   stage('Preparation'){
       git 'https://github.com/canindit75/JenkinsDemo.git'
       mvnHome = tool 'M3'
    }
   stage('Build'){
      withEnv(['%MAVEN_HOME%=$mvnHome']){
           bat(/"%MAVEN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package 
pause/)
      }
   }
}