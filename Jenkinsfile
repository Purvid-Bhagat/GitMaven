podTemplate(containers: [
  containerTemplate(
      name: 'maven', 
      image: 'maven:latest', 
      command: 'sleep', 
      args: '99d'
      )
  ], 
  
  volumes: [
  persistentVolumeClaim(
      mountPath: '/root/.m2/repository', 
      claimName: 'jenkins-pv-claim', 
      readOnly: false
      )
  ]) 

{
  node(POD_LABEL) {
 stage('Get a Maven project') {
 git 'https://github.com/dlambrig/simple-java-mavenapp.git'
 container('maven') {
 stage('Build a Maven project') {
 sh '''
echo "maven build"
mvn -B -DskipTests clean package
 '''
 }
      }
    }
  }
}
