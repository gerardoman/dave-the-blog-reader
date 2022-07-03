#!/usr/bin/env groovy
pipeline {
    agent any
    tools {
        nodejs "newman"
    }
    stages {
        stage('Run Newman Tests') {
            steps {
                sh 'npm install -g newman-reporter-htmlextra'
                sh 'newman run collections/Find-other-posts-by-the-author.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Find-other-posts-by-the-author.html"'
                sh 'newman run collections/Posts.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Posts.html"'
                sh 'newman run collections/Comments.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Comments.html"'
                sh 'newman run collections/Albums.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Albums.html"'
                sh 'newman run collections/Photos.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Photos.html"'
                sh 'newman run collections/Todos.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Todos.html"'
                sh 'newman run collections/Users.postman_collection.json -e environment/dave-the-blog-reader.postman_environment.json --suppress-exit-code 1 --reporters cli,htmlextra –-reporter-html-export "newman/Users.html"'
            }
        }
        stage('Publish Newman Reports') {
            steps {
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Find-other-posts-by-the-author.html',
                    reportName: 'Find other posts by the author Report'
                ]
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Posts.html',
                    reportName: 'Posts Report'
                ]
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Comments.html',
                    reportName: 'Comments Report'
                ]  
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Albums.html',
                    reportName: 'Albums Report'
                ]
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Photos.html',
                    reportName: 'Photos Report'
                ]
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Todos.html',
                    reportName: 'Todos Report'
                ]
                publishHTML target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: false,
                    keepAll: true,
                    reportDir: 'htmlreports',
                    reportFiles: 'Users.html',
                    reportName: 'Users Report'
                ] 
            }
        }
        stage('Run JMeter Tests') {
            steps {
                sh './jmeter/bin/jmeter.sh -n -t jmeter/extras/jenkins.jmx -l results.csv'

            }
        }
        stage('Publish JMeter Reports') {
            steps {
                perfReport filterRegex: '', relativeFailedThresholdNegative: 1.2, relativeFailedThresholdPositive: 1.89, relativeUnstableThresholdNegative: 1.8, relativeUnstableThresholdPositive: 1.5, sourceDataFiles: 'results.csv'
            }
        }
    }
}

