node("go") {
	stage('prepare') {
		checkout scm
		sh 'git submodule update --init --recursive --remote'
	}
	stage('build') {
		sh 'ln -s base16-schemes schemes'
		sh 'cd base16-builder-go && go build'
		// sh './base16-builder-go/base16-builder-go -schemes-dir base16-schemes'
	}
	stage('deploy') {
		sh 'test `git ls-files -m | wc -l` -gt 0'
		sh 'git add .'
		sh 'git commit -m "Update `date +%Y-%m-%d`"'
		sh 'git tag `date +Y-%m-%d`'
		sh 'git push github'
	}
}



// node("linux") {
//     stage('Execute') {
//	sh 'rm -rf output/'
//	sh 'pip install --user pybase16_builder'
//	sh 'ln -sf .local/bin bin'
//	checkout scm
//	sh 'pwd && ln -sF .. templates/vtrgb'
//	sh 'pybase16 update'
//	sh 'pybase16 build -t vtrgb -o output/'
//	archiveArtifacts artifacts: 'output/vtrgb/consolecolors/*.vga'
//     }
//     stage('deploy') {
//	sh 'test `git ls-files -m | wc -l` -gt 0'
//	sh 'git add .'
//	sh 'git commit -m "Update `date +%Y-%m-%d`"'
//	sh 'git tag `date +Y-%m-%d`'
//	sh 'git push github'
//     }
// }
