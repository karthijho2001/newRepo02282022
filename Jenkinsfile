
node {
    def mvnHome = tool 'Maven2'
    stage ("check out") {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '638e2ae6-4074-4a2f-a93e-9979509d4d9b', url: 
        'https://github.com/karthijho2001/newRepo02282022']]])
    }
    stage ("Build") {
        sh "${mvnHome}/bin/mvn clean install -f MyWebApp/pom.xml"
    }
    stage ("deploy on Tomcat") {
        deploy adapters: [tomcat9(credentialsId: '7dd3f787-d6bd-4472-b40b-9a32f9c2ad88', path: '', url: 'http://ec2-3-212-207-73.compute-1.amazonaws.com:8080')], contextPath: null, war: '**/*.war'
    }
}
