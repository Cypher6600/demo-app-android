pipeline {
    agent {
        kubernetes {
            yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: node
            image: node:16.13.1-alpine
            command:
            - cat
            tty: true
          - name: git
            image: alpine/git
            command:
            - sleep
            args:
            - infinity
          - name: fastlane
            image: softartdev/android-fastlane
            command:
            - sleep
            args:
            - infinity
            '''
        }
    }
    stages {
            stage('prep') {
                steps {
                git url: 'https://github.com/Cypher6600/demo-app-android.git', branch: 'second_remote'
                }
            }
            stage('fastlane') {
                steps{
                    container('fastlane') {
                        sh 'fastlane beta'
                       }
                    }
                }
            
    }
}
