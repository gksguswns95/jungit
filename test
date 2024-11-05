pipeline {
    agent any
    
    environment {
        GITHUB_CREDENTIALS = credentials('github-credentials-id') // Jenkins에 저장된 GitHub 자격증명 ID
    }
    
    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/your-username/your-repo.git', credentialsId: "${GITHUB_CREDENTIALS}"
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Node.js 프로젝트용 패키지 설치
                sh 'npm install'
            }
        }
        
        stage('Run Tests') {
            steps {
                // 테스트 실행 (테스트 파일이 있는 경우)
                sh 'npm test'
            }
        }
        
        stage('Build') {
            steps {
                // 빌드 명령 (예: Node.js 빌드 명령)
                sh 'npm run build'
            }
        }
        
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                // 실제 배포 스크립트 또는 명령어
                echo 'Deploying to production...'
            }
        }
    }
    
    post {
        always {
            // 빌드 후 언제나 실행될 작업 (예: 알림)
            echo 'Build process complete.'
        }
        success {
            // 빌드 성공 시 실행될 작업
            echo 'Build succeeded!'
        }
        failure {
            // 빌드 실패 시 실행될 작업
            echo 'Build failed!'
        }
    }
}
