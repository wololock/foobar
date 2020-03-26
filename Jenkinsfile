pipeline {
    agent any

    stages {
        stage("Deploy") {
            steps {
                script {
                    withCredentials([sshUserPrivateKey(credentialsId: "jenkins-deployment-key", keyFileVariable: "KEY")]) {
                        sh """
                            echo 'test\n' >> test.txt
                            git config --local user.name "Github"
                            git config --local user.email "bot@github.com"
                            git add test.txt
                            git commit -m "added test.txt"
                            git push git@github.com:wololock/foobar.git master
                        """
                    }
                }
            }
        }
    }
}
