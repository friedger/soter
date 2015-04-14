# AndroidCheckPlugin

Gradle plugin that adds support for Findbugs, Checkstyle and PMD to android projects.

## Usage

### Apply plugin

    buildscript {
        repositories {
            maven { url "http://repo.dlabs.si:8081/artifactory/simple/plugins-release-local/" }
        }
    
        dependencies {
            classpath 'com.github.blazsolar.gradle:soter:<version>'
        }
    }
    
    apply plugin: 'com.github.blazsolar.soter'
    
### Adding plugin rules

    dependencies {
        checkstyleRules "<checkstyle_rules>"
        findbugsRules "<findbugs_rules>"
        pmdRules "<pmd_rules>"
    }
    
### Configuration

    soter {
        
        checkstyle {
            enabled true
            uploadReports true
        }
    
        findbugs {
            enabled true
            uploadReports true
            reportLevel "low"
        }
        
        pmd {
            enabled true
            uploadReports true
        }
        
        logs {
            uploadReports true
        }
        
        tests {
            uploadReports true
        }

        docs {
            enabled true
            uploadReports true
        }

        codeCoverage {
            uploadReports true
        }
        
        publish {
            enabled true
        
            amazon {
                upload true
                variants = ["release"]
            }

            crashlytics {
                upload true
                variants = ["release"]
            }

        }
        
        notifications {
    
            enabled true
        
            hipchat {
                enabled true
                token "<hipchat_token>"
                roomId "<hipchat_room_id>"
                userId "<hipchat_user_id>"
            }
        
        }
        
        amazon {
            enabled true
            accessKey "<amazon_access_key>"
            secretKey "<amazon_secret_key>"
            bucket "<bucket>"
            path "path/in/amazon/bucket"
        }
        
        remote {
            pushToRemote true
            branch "<branch-to-push>" // current branch if `null`
            username "<username>"
            password "<passwird>"
        }
        
        afterAll {
            ghToken "<github_token>"
        }
        
    }
