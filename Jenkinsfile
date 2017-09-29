//SCM checkout -> Build/Launch -> Test -> Deploy

node {
    stage('Checkout') {
     checkout scm
	  //git url: 'https://github.com/raghupss/-java-mvn-hello-world-web-app.git'
  	echo 'hello from checkout'
    }
	 stage('Static Code Analysis') {
         mvn 'validate'
    }
         stage('Compile') {
         mvn 'compile'
    }
	stage('Test') {
         mvn 'test'
    }
	
	stage('Build') {
        mvn 'package'
    }
	
	
}

   def mvn(def args) {
    def mvnHome = tool 'M3'
    def javaHome = tool 'JDK8'
    withEnv(["JAVA_HOME=${javaHome}", "PATH+MAVEN=${mvnHome}/bin:${env.JAVA_HOME}/bin"]) {
        sh "${mvnHome}/bin/mvn ${args} --batch-mode -V -U -e -Dsurefire.useFile=false"
    }
}
