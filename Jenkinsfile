node("linux") {
    stage('Execute') {
        sh 'pip install --user pybase16_builder'
        sh 'ln -sf .local/bin bin'
        sh 'pybase16 update'
        checkout scm
        sh 'pwd && ln -sF .. templates/vtrgb'
        sh 'rm -rf output/'
        sh 'pybase16 build -t vtrgb -o output/'
        archiveArtifacts artifacts: 'output/vtrgb/consolecolors/*.vga'
    }
}
