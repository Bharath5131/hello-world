pipeline {
    agent any
    options{
        timeout(time: 10, unit: 'MINUTES')
    }
    
    environment{
        GIT = 'git'
    }
    
stages {
        stage('Fetch latest version from Pom'){
        steps{
            script{
                env.VERSION = sh(script: """cd $WORKSPACE/hello-world/; awk \'/<version>/; /<\\/version>/{exit}\' pom.xml | sed \'s/<.*>\\(.*\\)<\\/.*>/\\1/g\' | tr -d \'[:space:]\'""",returnStdout: true).trim()
                env.TARGET = "hello-world${VERSION}-${env.BUILD_NUMBER}"
                sh 'echo $TARGET'
            }
        }
    }
}
}
