node {
    def app

    stage('Clone repository') {
      git branch: 'main', credentialsId: 'github-token', url: 'https://github.com/rrrrrrrjk/kubernetes-manifest.git'
    }
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([string(credentialsId: 'github-token', variable: 'GIT_PAT')]) {
                        sh "git config user.email 'ryw.jakkraphat@gmail.com'"
                        sh "git config user.name 'rrrrrrrjk'"
                        sh "update"
                        
                        // View the current rolling-update.yml content
                        sh "cat rolling-update.yml"
                        
                        // Update the rolling-update.yml file with the new Docker tag
                        sh "sed -i 's+rywj/jenkins-react.*+rywj/jenkins-react:${DOCKERTAG}+g' rolling-update.yml"
                        sh "cat rolling-update.yml"  // View the updated content
                        
                        // Commit and push changes using PAT
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_PAT}@github.com/${GIT_USERNAME}/kubernetes-manifest.git HEAD:main"
                    }
                }
            }

    }
}