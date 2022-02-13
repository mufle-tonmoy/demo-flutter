pipeline {
    agent any

    stages {
        stage('initialization') {
            steps {
                echo('checking out')
                sh 'pwd'
                sh 'ls -al'
                echo('allowing execute permission')
                sh 'chmod +x build_apk.sh'
            }
        }
        stage('build') {
            environment {
                debugStorePassword = '909asKl1'
                debugKeyPassword = 'ajkl891a'
                debugKeyAlias = 'bkash_next_alias_0.0.1'
                debugStoreFile = 'keystore/bkash_next_debug.keystore'
            }
            steps {
                echo('building apk')
                withCredentials([gitUsernamePassword(credentialsId: 'my-github', gitToolName: 'default')]) {
                    sh './build_apk.sh'
                }
            }
        }
        stage('cleanup') {
            steps {
                echo('removing execute permission')
                sh 'chmod -x build_apk.sh'
            }
        }
        stage('distribute') {
            steps {
                echo('distributing out')
            }
        }
    }
}
