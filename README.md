C# Quick start Sample for Instant Buy API
Copyright (c) 2013 Google Inc.

## Quick Start sample for Instant Buy API
This sample shows the minimal integration for Google InstantBuy in C#.

### Setup
You'll need to fill in information in two files before the APIs function correctly.
In InstantBuySample/index.html add your OAuth Client Id as OauthClientId
In InstantBuySample/Web.config add your InstantBuy Id and Secret for the sandbox environment and your OAuth Client Id.

### Running the sample
To run this application open the solution in MonoDevelop or Visual Studio run and browse to localhost:8080
- or -
run xsp in the InstantBuySample subdirectory.

### About the sample
There are two components namely the index.html page and http handlers.

The index.html page contains all of the JavaScript to demonstrate client side calls to the Instant Buy APIs.

The flow is describe below:
Request Masked Wallet Request Jwt from server
Generate Wallet button based on Masked Wallet Jwt
Add button to page
Clicking on the button initiates the Masked Wallet flow
Masked Wallet flow returns obfuscated billing information and shipping address
Send Masked Wallet Response Jwt to server to generate Full Wallet Request Jwt
Request Full Wallet from Google
Full Wallet Response returns one time primary account number, cvc, billing information, and shipping information
Send Full Wallet Response Jwt to server to generate Transaction Status Notification
Send Transaction Status Notification to Google

The http handlers generate their respective Jwts based on the responses passed in.
MaskedHandler generates the Masked Wallet Request Jwt
FullHandler generates the Full Wallet Request Jwt
NotifyHandler generates the Transaction Status Notification Jwt

The handlers use a builder pattern to create the WalletBody.

Web.config defines the URL paths that map to the handlers.
