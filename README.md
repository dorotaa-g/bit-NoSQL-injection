# BIT-NoSQL-injection
Subject: Information Technologies Security (BIT_I)

Year: 2022/2023 (winter semester)

This repository contains all the files needed to build and run two vulnerable applications - Owasp Juice Shop (https://github.com/juice-shop/juice-shop) , nosqlinjection (https://github.com/standash/damn-vulnerable-web-apps/tree/master/apps/nosqlinjection) .

Applications were used as part of a school project to demonstrate the severity of a nosql injection vulnerability.

## Manual
Application OWASP Juice Shop was built and run locally on virtual machine (Kali Linux):
1. Install a 64bit node.js
2. Download application (juice-shop-14.3.1_node18_linux_x64.tgz) from repository as a zip from https://github.com/juice-shop/juice-shop/releases/tag/v14.3.1
3. Unpack and go to application directory
4. Run npm start
5. Go to http://localhost:3000

Application nosqlinjection from damn-vulnerable-web-apps was built and run locally on MacOS:
1. Install a Docker 4.13.1
2. Download application from repository - git clone https://github.com/standash/damn-vulnerable-web-apps
3. Build the application and run it through ./run.py nosqlinjection 8888 80
4. Go to http://localhost/login.html

## NoSQL injection attacks manual
### Exfiltration of orders database (OWASP Juice Shop)
1. Register on Juice Shop website
2. Create an order
3. Go to order tracking (http://localhost:3000/#/track-result/new?id=xxxx-xxxxxxxxxxxxxxxx)
4. Enter the malicious code in id parameter in URL - ' 1==1 '
5. Find all of the orders via Dev Tools

### Simple DoS attack (OWASP Juice Shop)
1. Register on Juice Shop website
2. Open any product and submit review
3. Edit the review 
4. Browse requests and responses in Dev Tools and find the filename path (/rest/products/2/reviews)
5. Change 2 to function sleep(1000) and build new URL address
6. Go to http://localhost:3000//rest/products/sleep(1000)/reviews

### Login without password (nosqlinjection)
1. Username is Batman
2. Enter the malicious code in the username field - Batman’, pword: {$gt: ”} }) //

## Resources
https://github.com/juice-shop/juice-shop

https://github.com/standash/damn-vulnerable-web-apps/tree/master/apps/nosqlinjection
