# Spectra Plugin For Jenkins - Build Steps / Post-build Actions / Pipeline

-   Spectra plugin for Jenkins helps you integrate Spectra's automated audit process into your project CI/CD flow.
-   Check "spectra\_guide" in this repository for details.

## Set up

-   Obtain your API key from [Spectra website](https://spectra-space.io/)
-   Run Jenkins
-   Manage Jenkins > Manage Plugins > Advanced Settings > Deploy Plugin > Select File
-   Select "spectra-plugin.hpi" in [Spectra plugin repository](https://github.com/spark63/Jenkins-Plugin) and deploy.

## Apply to Freestyle Project

-   After installation, you will find "Spectra" in "Build Steps" and "Post-build Actions"
    -   They work same, so you may use it depending on your CI procedure
-   Put API key

## Apply to Pipeline Project

-   place `step([$class: 'SpectraBuilder', apikey: {apikey}])` in any stage you want in your pipeline script.

```shell
pipeline {
    agent any
    stages {
        stage('Stage A') {
          ...
        }
        stage('Spectra') {
            steps {
                step([$class: 'SpectraBuilder', apikey: 'abcd1234'])
            }
        }
        stage('Stage B') {
          ...
        }
    }
}

```

## Build Result and Email Notification

-   In the case of build fail, you may check 'Console Output' from Jenkins.
    -   Invalid API key causes build failure.
-   Once your audit is complete, the audit result will be sent to your email set in Spectra website.
