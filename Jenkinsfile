#!/usr/bin/env groovy

node {
	stage('checkout') {
		deleteDir()
	}
	stage('checkout') {
		checkout scm
	}
	stage('Clean') {
		withMaven(jdk: 'java-11', maven: 'maven') {
			sh "mvn clean -T100"
		}
	}
	stage('Package') {
		withMaven(jdk: 'java-11', maven: 'maven') {
			sh "mvn -Pjib verify package jib:build"
		}
	}
	stage("Deploy") {
		build 'springdoc-openapi-demos-deploy'
	}
}
