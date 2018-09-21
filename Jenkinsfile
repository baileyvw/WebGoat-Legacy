pipeline {
	agent {
		docker {
			image 'maven:3-alpine'
			args '-v /root/.m2:/root/.m2'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'mvn -B -DskipTests clean package'
			}
		}
		stage('Dependency Check') {
			steps {
				dependencyCheckAnalyzer datadir: 'dependency-check-data', includeVulnReports: true, hintsFile: '', includeCsvReports: false, includeHtmlReports: true, includeJsonReports: false, isAutoupdateDisabled: false, outdir: '', scanpath: '', skipOnScmChange: false, skipOnUpstreamChange: false, suppressionFile: '', zipExtensions: ''
                
    		        	dependencyCheckPublisher canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''

            			archiveArtifacts allowEmptyArchive: true, artifacts: '**/dependency-check-report.html'
                
                    		archiveArtifacts allowEmptyArchive: true, artifacts: '**/dependency-check-report.xml'
			}
		}
	}
}
