=Multistep docker build=
This example has no practical use and demonstrates an example of multi step docker build.

This example generates and executes [https://www.jhipster.tech/](JHipser) application from JDL file in 3 steps:
1. Use node.js docker image to install JHipster and generate application from JDL
2. Use Maven docker image to build generated application
3. Build final executable image using Open JDK docker image

How to generate and run image: 
1. docker build -t jh-demo-app .
2. docker run -it -p 8080:8080 jh-demo-app
3. Open http://localhost:8080/ in browser