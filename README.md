Spring Security OAuth2 Google Plugin
====================================
Upgrade for Grails 5 compatibility (Grails 5.3.5 & Gradle 7.2)

[![Build Status](https://travis-ci.org/robfletcher/grails-spring-security-oauth2-google.svg?branch=master)](https://travis-ci.org/robfletcher/grails-spring-security-oauth2-google)
Add a Google OAuth2 provider to the [Spring Security OAuth2 Plugin](https://github.com/grails-plugins/grails-spring-security-oauth2).

Installation
------------
Add the following dependencies in `build.gradle`
```
dependencies {
...
    compile 'org.grails.plugins:spring-security-oauth2:3.0.0'
    compile 'org.grails.plugins:spring-security-oauth2-google:5.3.5'
...
}
```

Usage
-----
Add this to your application.yml
```
grails:
    plugin:
        springsecurity:
            oauth2:
                providers:
                    google:
                        api_key: 'google-api-key'               #needed
                        api_secret: 'google-api-secret'         #needed
                        successUri: "/oauth2/google/success"    #optional
                        failureUri: "/oauth2/google/failure"    #optional
                        callback: "/oauth2/google/callback"     #optional
                        scopes: "some_scope"                    #optional, see https://developers.google.com/identity/protocols/googlescopes#monitoringv3
```
You can replace the URIs with your own controller implementation.

In your view you can use the taglib exposed from this plugin and from OAuth plugin to create links and to know if the user is authenticated with a given provider:
```xml
<oauth2:connect provider="google" id="google-connect-link">Google</oauth2:connect>

Logged with google?
<oauth2:ifLoggedInWith provider="google">yes</oauth2:ifLoggedInWith>
<oauth2:ifNotLoggedInWith provider="google">no</oauth2:ifNotLoggedInWith>
```
License
-------
Apache 2
