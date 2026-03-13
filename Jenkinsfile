pipeline{
    agent any
    
    options{
        timestamps()
        timeout(time: 5, unit: 'MINUTES')
    }

    stages{
        stage("make directory"){
            options{
                retry(2)
            }
            steps{
                sh """
                    if [ ! -d jenkins-tutorial-test ]; then
                        mkdir jenkins-tutorial-test
                    else 
                        echo 'not built'
                    fi
                """
            }
        }

        stage("make a file"){
            steps{
                sh "touch jenkins-tutorial-test/file1.txt"
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'jenkins-tutorial-test/*.txt', allowEmptyArchive: true
        }
    } 
}
