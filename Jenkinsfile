pipeline {
	agent { node { label 'ansible' } }
	stages {
		stage('yamllint') {
			steps {
				ansiColor('xterm') {
					sh 'yamllint .'
				}
			}
		}
		stage('ansible-lint') {
			steps {
				ansiColor('xterm') {
					sh '''#!/bin/bash -xe
					find -name '*.yml' >scripts
					mapfile -t scripts <scripts
					rm -f scripts
					ansible-lint --force-color "${scripts[@]}"
					'''
				}
			}
		}
	}
}
// vim: filetype=groovy
