# Vulnerable postMessage() Lab

## Setup
 1. In your /etc/hosts file, add `127.0.0.1	child.window parent.window`
 2. Clone the directory and cd into it.
 3. Run `python -m SimpleHTTPServer`
 4. Go to **http://parent.window:8000/parent** to test the 2 added vulnerabilities.

## Vulnerabilities
Two vulnerabilities have been added, namely:
 1. Sender's origin not verified.
 2. targetOrigin not specified.

## Exploitation instructions
If you go through the JS code of the pages, you will see that the following vulnerabilities exist:
 1. In lab 1, a message is sent from the main application (parent window) to the contact form (child window). This message contains the user's personal details from the parent window, and populates the contact form. Your goal here is to achieve XSS by sending a malicious message to window containing the contact form.
 2. In lab 2, the message is sent from the child window to the parent window. The message here takes the login details (from the child window) and posts it to the parent window. Your goal here is to setup an attacker website which will steal the login details of the user from the aforementioned login page.

To exploit both these vulnerabilities: 
 1. Add your custom entry in /etc/hosts eg. `127.0.0.1 attacker.window`.
 2. Make a new directory and add your HTML page with the JS exploit.
 3. With the above simpleHTTPServer already running, run `python -m SimpleHTTPServer <port-here>`
 4. Go to http://attacker.window:<port-from-above>/ and access your exploit page.

The complete exploit demonstration can be viewed from Farah Hawa's [youtube video for postMessage()](https://youtu.be/CWNxoxOX6sI).
