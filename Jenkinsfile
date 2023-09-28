pipeline {
    agent none
    stages {
        stage("Build") {
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps{
                script {
                    def data = [
                        "firstName" : "Azzam",
                        "lastName" : "Imran"
                    ]
                    writeJSON(file: "data.json", json:data)
                }
                echo("Start Build")
                sh("./mvnw clean compile test-compile")
                echo ("Finish Build")
            }
        }
        stage("Test") {
            agent {
                node {
                    label "linux && java11"
                }
            }
            steps{
                echo("Start Test")
                sh("./mvnw test")
                echo ("Finish Test")
            }
        }
        stage("Deploy") {
            steps{
                echo("Hello Deploy 1")
                sleep(5)
                echo("Hello Deploy 2")
                echo("Hello Deploy 3")
            }
        }                
    }
    
    post {
        always {
            echo "I always say Hello again!"
        }
        success {
            echo "Yay, success"
        }
        failure {
            echo "Oh no, failure"
        }
        cleanup {
            echo "Don't care success or error"
        }
    }
}