pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/vrushabh-chougale/vrushabh-chougale-site.git', credentialsId: 'github-pat'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                sudo cp -r build/* /var/www/vrushabhchougale.site/
                sudo systemctl restart nginx
                '''
            }
        }
    }
}
