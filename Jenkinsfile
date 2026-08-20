node{
    def MavenHome=tool name: "maven-3.9.16"
    stage('git checkout'){
      git branch :'master', url: 'https://github.com/nikhitha-narra-26/maven-webapplication-project-kkfunda.git'
    }
    stage('compile'){
        sh " ${MavenHome}/bin/mvn compile "
    }
    stage('Build'){
        sh " ${MavenHome}/bin/mvn clean package "
    }
    stage('SQ Report'){
        sh " ${MavenHome}/bin/mvn sonar:sonar "
    }
     stage('Deploy to nexus'){
            sh " ${MavenHome}/bin/mvn clean deploy"
     }
     stage('deploy to tomact'){
     sh """ curl -u kk:Password \
--upload-file /var/lib/jenkins/workspace/scripted-way-pipeline/target/maven-web-application.war \
"http://98.82.199.108:8080/manager/text/deploy?path=/maven-web-application&update=true"
"""
    }
}
