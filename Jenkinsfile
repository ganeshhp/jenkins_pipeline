pipeline { 
    agent { dockerContainer { image 'maven:3.8.1-adoptopenjdk-11'} }
    stages {
        stage('SCM_Chekout') { 
            steps { 
                checkout([$class: 'GitSCM', 
                    branches: [[name: '*/master']], 
                    doGenerateSubmoduleConfigurations: false, 
                    extensions: [], 
                    submoduleCfg: [], 
                    userRemoteConfigs: [[url: 'https://github.com/ganeshhp/helloworldweb.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -f pom.xml clean package' 
            }
        }

	   stage('deploy') {
            steps {
                sh 'curl -uuser1:cmVmdGtuOjAxOjE3NDA4MDkwNzM6RmVTajNjanBkM3hFRVlkQ2szWm1RR1ZiYlRn -T target/Helloworldwebapp-dev.war "https://scanvas.jfrog.io/artifactory/webapp-1-generic-local/Helloworld-docker.war"'
            }
       }
    }
}
