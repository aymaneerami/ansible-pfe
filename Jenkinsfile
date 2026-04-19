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
               
                sh '/usr/bin/ansible-playbook -i hosts apache_php.yml -u ansible'
            }
        }
        stage('Configure Load Balancer') {
            steps {
                sh '/usr/bin/ansible-playbook -i hosts loadbalancer.yml --become'
            }
        }
    }
}
