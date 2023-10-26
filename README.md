# EnableX Programmable Voice API: Outbound Calls Client Examples and Setup Guide

Explore Essential Client Examples for Illustrating Outbound Calls with Enablex Programmable Voice APIs. 

Prerequisite Checklist: 
Enablex Application Credentials: Ensure you have your APP ID and APP KEY readily available. You can obtain these credentials by registering with EnableX at https://portal.enablex.io/cpaas/trial-sign-up/. 
Hosting Environment: Secure a suitable hosting environment, whether it's on the cloud or a local machine. 

These instructions provide a step-by-step guide on how to initiate Outbound Calls, utilizing the powerful capabilities of Enablex Programmable Voice APIs. 

## Installation
- `git clone https://github.com/EnableX/voice-api-outbound-video-room.git`
- `cd voice-api-outbound-video-room`
- `npm install`


## Setting up configurations using environment variables

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the = with values from your EnableX account:

- Set APP ID and APP KEY. It is required configuration.
  - `export ENABLEX_APP_ID=`
  - `export ENABLEX_APP_KEY=`

- Set port. Default port is set to 3000. It is an optional configuration.
  - `export SERVICE_PORT=`

For Windows:
  - Make a file with name ".env" in root directory . And copy content of .env.example in .env file . Then set the value of these variables.
  - `ENABLEX_APP_ID` , `ENABLEX_APP_KEY` , `SERVICE_PORT` 

## Webhook - EnableX will send HTTP requests to your application (`/event`) after certain events occur.

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the = with values from your EnableX account:

- If you have deployed this service on a web server which is publicly accessible, set the public URL. Example - `https://{PUBLIC_URL}`
  - `export PUBLIC_WEBHOOK_URL=`
- If you want to test this service on a web server running locally on your own computer at a given port, with ngrok, you can generate URL that tunnels requests to your web server running locally. Once ngrok installed, run following -
  - `./ngrok http {SERVICE_PORT}` . It should provide you a ngrok URL something similar to `https://fc6c892d6cd7.ngrok.io`. Now, Set the ngrok URL. Example - `https://fc6c892d6cd7.ngrok.io`
    - `export PUBLIC_WEBHOOK_URL=`
- Set to run the service on http / https (false / true)
  - `export LISTEN_SSL=`

  For Windows:
  - In that .env file set these variables `USE_PUBLIC_WEBHOOK`, `LISTEN_SSL`.
  - Their explanation is given in Linux/Mac section (Upper section).


## SSL Certificate (Self Signed or Registered). It is required configuration if LISTEN_SSL is set to true.

  For Linux/Mac:
  - Make a directory called certs on the root of the project
    - `mkdir certs`
  - Change to certs directory
    - `cd certs`
  - Create and Install certificates
    - `sudo openssl req -nodes -new -x509   -keyout example.key -out example.crt   -days 365   -subj '/CN=example.com/O=My Company Name LTD./C=US'; cat example.crt > example.ca-bundle`
  - use the certificate .key [self signed or registered]
    - `export CERTIFICATE_SSL_KEY=`
  - use the certificate .crt [self signed or registered]
    - `export CERTIFICATE_SSL_CERT=`
  - use the certificate CA[chain] [self signed or registered]
    - `export CERTIFICATE_SSL_CACERTS=`
  - switch to the root of the project
    - `cd ..`
 
For Windows (Using Git Bash):
  - Make a directory called certs on the root of the project
    - `mkdir certs`
  - Change to certs directory
    - `cd certs`
  - Create and Install certificates
    - `openssl req -nodes -new -x509   -keyout example.key -out example.crt   -days 365` 
    - `cat example.crt > example.ca-bundle`
  - Update these fields manually in .env file if not given else you can ignore it. 
    - use the certificate .key [self signed or registered]
      - `CERTIFICATE_SSL_KEY=`
    - use the certificate .crt [self signed or registered]
      - `CERTIFICATE_SSL_CERT=`
    - use the certificate CA[chain] [self signed or  registered]
      - `CERTIFICATE_SSL_CACERTS=`
  - switch to the root of the project
    - `cd ..`


## Starting the client application script
- For Outbound Calls,
  - `node client-outbound-videoroom.js`
