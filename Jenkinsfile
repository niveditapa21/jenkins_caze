pipeline {
    agent any

    stages {
        stage('Basic Environment Check') {
            steps {
                sh '''
                echo "=== Basic Environment Check ==="
                echo "Current Directory: $(pwd)"
                echo "Logged-in User: $(whoami)"
                uname -a
                df -h
                '''
            }
        }

        stage('File Operations Test') {
            steps {
                sh '''
                echo "=== File Operations Test ==="
                echo "This is a test file for Jenkins job." > testfile.txt
                echo "Contents of the test file:"
                cat testfile.txt
                mv testfile.txt renamed_testfile.txt
                echo "File renamed to renamed_testfile.txt"
                rm renamed_testfile.txt
                echo "File deleted: renamed_testfile.txt"
                '''
            }
        }

        stage('Network Connectivity Test') {
            steps {
                sh '''
                echo "=== Network Connectivity Test ==="
                ping -c 4 google.com
                curl -I https://www.google.com
                echo "Network connectivity test completed!"
                '''
            }
        }

        stage('Build Simulation') {
            steps {
                sh '''
                echo "=== Build Simulation ==="
                mkdir -p build
                cd build
                touch main.o utils.o program.bin
                echo "Build files created:"
                ls -la
                cd ..
                rm -rf build
                echo "Build simulation completed!"
                '''
            }
        }
    }
}
