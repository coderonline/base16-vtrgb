node("go") {
	stage('prepare') {
		checkout scm
		sh 'git submodule update --init --recursive --remote'
	}
	stage('build') {
		sh './build.sh'
	}
	stage('deploy') {
		sh 'test `git ls-files -mo consolecolors | wc -l` -gt 0'
		sh 'git add .'
		sh 'git commit -m "Update `date +%Y-%m-%d`"'
		sh 'git tag `date +%Y-%m-%d`'
		sh 'git remote add github git@github.com:coderonline/base16-vtrgb.git || echo WARNING: Ignored an error.'
		sh 'git push github HEAD:master'
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
