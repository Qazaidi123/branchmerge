pipeline {
    agent any
    
    stages {

        stage ("Clone Git repo") {
            steps {
               git url: "https://github.com/Qazaidi123/branchmerge.git", credentailsID: "git-creds", branch: "main"
            }
        }

        stage ("Merge developer branch to main") {
            steps {
                withCredentials ([usernamePassword(
                    credentailsID: "git-creds",
                    usernameVariable: "GIT_USER",
                    passwordVariable: "GIT_PASS"
                )]) {
                    sh '''
                    git config user.name "jenkins"
                    git config user.email "jenkins@example.com"
                    git remote set-url origin https://$GIT_USER:$GIT_PASS@github.com/Qazaidi123/branchmerge.git
                    git checkout main
                    git pull origin main
                    git merge -X ours origin/developer
                    git push origin main
                     
                }
                }
            }
        }
    }
    }
