# Fake SMTP Server
[![Build Status](https://travis-ci.org/gessnerfl/fake-smtp-server.svg?branch=master)](https://travis-ci.org/gessnerfl/fake-smtp-server)

*Simple SMTP Server which stores all received emails in an in-memory database and renders the emails in a web interface*

## Introduction

The Fake SMTP Server is a simple SMTP server which is designed for development purposes. The server collects all
received emails, stores the emails in an in-memory database and provides access to the emails via a web interface.

There is no POP3 or IMAP interface included by intention. The basic idea for this software is that it is used during 
development to configure the server as target mail server. Instead of sending the emails to a real SMTP server which 
would forward the mails to the target recipient or reject test emails (e.g. @example.com mails) the server just accepts
all mails, stores the in the database so that they can be rendered in the UI. This allows you to use any test mail and
check the sent email in the web application of the Fake SMTP Server.

# Configuration

As the application is based on Spring Boot the same rules applies to the configuration as described in the Spring Boot 
Documentation (http://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#boot-features-external-config).

The configuration file application.properties can be placed next to the application jar, in a sub-directory config or 
in any other location when specifying the location with the parameter `-Dspring.config.location=<path to config file>`.

The following paragraphs describe the application specific resp. pre-defined configuration parameters. If more 
configuration e.g. authentication is needed please check the Spring Boot Documentation for more detail.

## Fake SMTP Server
The following snippet shows the configuration of a broker with its default values. You can configure different brokers by using different broker names.

    fakesmtp.port=5025      #The SMTP Server Port used by the Fake SMTP Server
    fakesmtp.bindAddress    #The binding address of the Fake SMTP Server; By default it is bound to all interfaces

## Web UI
The following snippet shows the pre-defined web application configuration

    server.port=5080     #Port of the web interface
    management.port=5081 #Port of the http management api
