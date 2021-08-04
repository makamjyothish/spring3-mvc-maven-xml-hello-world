pipeline {
    agent any
   
      tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven3"
    }

    stages {
        stage('scm') {
            steps {
             git credentialsId: 'github_credentials', url: 'https://github.com/makamjyothish/spring3-mvc-maven-xml-hello-world.git'   
            }
        }
        stage('build') {
            steps {
                // maven packages
            sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
           }
        stage ('Artifacts') {
            steps {
                // artifacts war file
                  archiveArtifacts 'target/*.war'
                }
           }
          stage ('diploy') {
            steps {
               
                                 withCredentials([usernameColonPassword(credentialsId: 'tomcat_credential', variable: 'riyo')]) {sh "curl -v -u ${riyo} -T /var/lib/jenkins/workspace/spring3/target/spring3-mvc-maven-xml-hello-world-1.0-SNAPSHOT.war 'http://13.126.18.165:8081//manager/text/deploy?path=/money007&update=true'"           
}
                
                }
           } 
    }
}
