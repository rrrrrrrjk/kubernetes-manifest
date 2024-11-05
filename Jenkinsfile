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
                    sh "echo ${env.BUILD_NUMBER} > build_number.txt"

                    
                    // Commit and push changes using PAT
                    sh "git add build_number.txt"
                    sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                    sh "git push https://github.com/rrrrrrrjk/kubernetes-manifest.git"
                }
            }

    }
}