#README Node js

Node is java script running on server. Uses non blocking IO model. IS fast and efficient. Works on Asynchronus.

Express js is framework for nodjs.

NPM is node package module. If you write npm install express, It will download express module in node_modules folder.

Package.json: tells how your package is structured and what to do to install it

npm init
npm install --save expressi  ## save dependency in package.json
npm install --save nodemon
npm run start


docker build -t node-docker-tutorial .
docker run -it -p 9001:3000 -v $(pwd):/app node-docker-tuorial

https://tutorialedge.net/docker/working-with-docker-nodejs/
https://www.youtube.com/watch?v=CsWoMpK3EtE

