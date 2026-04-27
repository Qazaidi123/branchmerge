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

            }
}
