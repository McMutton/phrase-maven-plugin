# Phrase Maven Plugin
[![Build Status](https://travis-ci.org/mytaxi/phrase-maven-plugin.svg?branch=master)](https://travis-ci.org/mytaxi/phrase-maven-plugin)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.mytaxi.maven.plugins/phrase-plugin/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.mytaxi.maven.plugins/phrase-plugin)

## What is this?
This projects contains a maven plugin to download PhraseApp translations due the 
build process from [PhraseApp API v2](http://docs.phraseapp.com/api/v2/).

## What you have to do to start it with maven?

### Create the bean PhraseAppSyncTask to run this job scheduled lately.

    Configure the maven plugin
    
    <plugin>
        <groupId>com.mytaxi.maven.plugins</groupId>
        <artifactId>phrase-plugin</artifactId>
        <version>1.0.0</version>
        <configuration>
            <authToken>YOUR_AUTH_TOKEN(REQUIRED)</authToken>
            <projectId>YOUR_PROJECT_ID(REQUIRED)</projectId>
            
            <generatedResourcesFolderName>YOUR_GENERATED_RESOURCE_FOLDER(default:generated-resources/)</generatedResourcesFolderName>
            <messagesFolderName>YOUR_MESSAGES_FOLDERNAME(default:messages/)</messagesFolderName>
            <messageFilePrefix>YOUR_MESSAGE_FILE_PREFIX(default:messages_)</messageFilePrefix>
            <messageFilePostfix>YOUR_MESSAGE_FILE_POSTFIX(default:.properties)</messageFilePostfix> 
            <branches>
                <branch>BRANCH_YOU_WANT_TO_WORK_WITH(defaut:master)</branch>
            </branches>
        </configuration>
        <executions>
            <execution>
                <goals>
                    <goal>phrase</goal>
                </goals>
            </execution>
        </executions>
    </plugin>

### Branch configuration guide

In order to work only with the master phraseapp branch, either skip the branch configuration completely, or have the following:

    <branches>
        <branch>master</branch>
    </branches>
    
To work with multiple branches, list them all (including the master branch if you want to work with it) under the `<branches>` tag. 
   
    <branches>
        <branch>master</branch>
        <branch>temp</branch>
        <branch>demo</demo>
    </branches>
