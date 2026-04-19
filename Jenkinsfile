pipeline {
    agent any

    stages {
        stage('Pull Code from Git') {
            steps {
                checkout scm
            }
        }

        stage('Deploy Web Servers') {
            steps {
                // كيطبق الـ Playbook على السيرفورات بجوج
                sh 'ansible-playbook -i hosts apache_php.yml -u ansible'
            }
        }

        stage('Configure Load Balancer') {
            steps {
                // كيقاد Nginx فـ الماكينة Lab
                sh 'ansible-playbook -i hosts loadbalancer.yml --become'
            }
        }
    }
}
