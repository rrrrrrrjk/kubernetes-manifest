node {
    def app

    stage('Clone repository') {
      git branch: 'main', credentialsId: 'github-token', url: 'https://github.com/rrrrrrrjk/kubernetes-manifest.git'
    }
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    // Configure Git user
                    sh "git config user.email 'ryw.jakkraphat@gmail.com'"
                    sh "git config user.name 'rrrrrrrjk'"
                    
                    // View the current rolling-update.yml content
                    sh "cat update/rolling-update.yml"
                    
                    // Update the rolling-update.yml file with the new Docker tag
                    sh "sed -i 's+rywj/jenkins-react.*+rywj/jenkins-react:${DOCKERTAG}+g' update/rolling-update.yml"
                    
                    // View the updated content
                    sh "cat update/rolling-update.yml"
                    
                    // Commit and push changes using PAT
                    sh "git add update/rolling-update.yml"
                    sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/rrrrrrrjk/kubernetes-manifest.git HEAD:main"
                }
            }

    }
}