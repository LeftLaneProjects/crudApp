node{
    
    stage("clone"){
            git branch: env.BRANCH_NAME, url: '$github_url'
    }
     stage("build"){
        def mavenHome = tool name: "Maven363", type: "maven"
        def mavenCMD = "${mavenHome}/bin/mvn "
        sh "${mavenCMD} clean package"
    }
    /**stage("deploy"){
        def pom = readMavenPom file: 'pom.xml'
        filesByGlob = findFiles(glob: "target/*.${pom.packaging}");
	artifactPath = filesByGlob[0].path;
        echo "Path: ${artifactPath}"
	switch(env.BRANCH_NAME){
		case "develop":
			nexusArtifactUploader artifacts: [[artifactId: pom.artifactId, classifier: '', file: artifactPath, type: pom.packaging]], credentialsId: 'NEXUS_CREDENTIALS', groupId: pom.groupId, nexusUrl: '$nexus_url', nexusVersion: 'nexus3', protocol: 'http', repository: 'dev', version: pom.version
		    	break
		case "release":
			nexusArtifactUploader artifacts: [[artifactId: pom.artifactId, classifier: '', file: artifactPath, type: pom.packaging]], credentialsId: 'NEXUS_CREDENTIALS', groupId: pom.groupId, nexusUrl: '$nexus_url', nexusVersion: 'nexus3', protocol: 'http', repository: 'qa', version: pom.version
			break
		case "master":
			nexusArtifactUploader artifacts: [[artifactId: pom.artifactId, classifier: '', file: artifactPath, type: pom.packaging]], credentialsId: 'NEXUS_CREDENTIALS', groupId: pom.groupId, nexusUrl: '$nexus_url', nexusVersion: 'nexus3', protocol: 'http', repository: 'stage', version: pom.version
			break
		default:
			nexusArtifactUploader artifacts: [[artifactId: pom.artifactId, classifier: '', file: artifactPath, type: pom.packaging]], credentialsId: 'NEXUS_CREDENTIALS', groupId: pom.groupId, nexusUrl: '$nexus_url', nexusVersion: 'nexus3', protocol: 'http', repository: 'prod', version: pom.version
			break
	}
    }**/
}
