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
If you go through the JS code of the pages, you will see that the above vulnerabilities exist in their respective pages:
 1. In http://child.window:8000/child/login.html, the child window, you will see that the targetOrigin is not specified.
 2. In http://child.window:8000/child/contact.html, the child window, you will see that the sender's origin is not verified.

To exploit both these vulnerabilities, you can add your custom entry in /etc/hosts eg. `127.0.0.1 attacker.window` and add your own exploit code in JS, or refer to the added JS exploit codes in the repo.

The exploits can also be refered from Farah Hawa's [youtube video for postMessage()](https://youtu.be/CWNxoxOX6sI).
