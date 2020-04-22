node {
   def var1
   stage('checkout_sourcecode') { 
      
      git 'https://github.com/jglick/simple-maven-project-with-tests.git'
             
      var1 = tool 'MAVEN_HOME'
   }
   stage('Build_artifact') {
      
      withEnv(["var2=$var1"]) {
         if (isUnix()) {
            sh '"$var2/bin/mvn" -DskipTests clean package'
         } else {
            bat(/"%var2%\bin\mvn" -DskipTests clean package/)
         }
      }
   }
   stage('Publish_reports') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
}
