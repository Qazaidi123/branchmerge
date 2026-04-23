pipeline {
    agent any

    environment {
        DEV_BRANCH = "developer"
        REPO_URL = "https://github.com/Qazaidi123/branchmerge.git"
    }

    stages {

        stage("Clone Git repo") {
            steps {
                git url: "${REPO_URL}",
                    credentialsId: "git-creds",
                    branch: "main"
            }
        }

        stage("Merge developer branch to main") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: "git-creds",
                    usernameVariable: "GIT_USER",
                    passwordVariable: "GIT_PASS"
                )]) {
                    sh '''
                    git config user.name "jenkins"
                    git config user.email "jenkins@example.com"

                    git remote set-url origin https://$GIT_USER:$GIT_PASS@github.com/Qazaidi123/branchmerge.git

                    git fetch origin

                    git checkout main
                    git pull origin main

                    git merge origin/${DEV_BRANCH}

                    git push origin main
                    '''
                }
            }
        }
    }
}
