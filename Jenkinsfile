node("linux") {
    stage('Execute') {
        sh 'rm -rf output/'
        sh 'pip install --user pybase16_builder'
        sh 'ln -sf .local/bin bin'
        checkout scm
        sh 'pwd && ln -sF .. templates/vtrgb'
        sh 'pybase16 update'
        sh 'pybase16 build -t vtrgb -o output/'
        archiveArtifacts artifacts: 'output/vtrgb/consolecolors/*.vga'
    }
}
