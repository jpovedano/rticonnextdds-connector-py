pipeline{
    agent none
    stages{
        stage("Test"){
            parallel {
                stage("Linux x64") {
                    agent {
                        label "x64Linux2.6gcc4.4.5"
                    }
                    steps {
                        withPythonEnv("python") {
                            sh "tox"
                        }
                    }
                }
                stage("Darwin x64") {
                    agent {
                        label "x64Darwin17clang9.0"
                    }
                    steps {
                        withPythonEnv("python") {
                            sh "tox"
                        }
                    }
                }
                stage("Windows x64") {
                    agent {
                        label "x64Win64VS2012"
                    }
                    steps {
                        withPythonEnv("python3") {
                            sh "tox"
                        }
                    }
                }
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}