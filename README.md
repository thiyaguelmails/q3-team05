DevOps & CNA Q3 Training Tests
==============================

This is a shell project to run basic API tests against the Q3 DevOps & CNA
training project.

Getting Started (with sample code)
----------------------------------

The sample service implementation in this project is written in Node.js, but
that is not a requirement, it's simply a sample.  Any programming language,
platform, or packaging mechanism may be used for the project, as long as the
REST services satisfy the tests in this package.

It's probably a good idea to run up the sample code once to see the expected service signatures.

To run the sample Node.js code:

1. Install Node.js

2. Install all dependencies with "npm install"

3. (Recommended) Install nodemon with "npm install -g nodemon"
You can then run "nodemon ." to run the sample code.

Notes on the Sample Code
------------------------

There are //TODO comments in the code where there features that have not been 
implemented (assuming you wish to start from this codebase; as we've said, you 
can implement in any language.)

The sample code is a monolith, not true micro services.  A proper CNA app should
be refactored into independent, separately running services. That task is left
for teams to take on.

The sample code stores data in an in-memory database.  That will not be required
when all services are fully implemented.

Running the Tests
-----------------

The tests are implemented with Soap UI.  In order to run the tests, first ensure
there is a REST server running with implementations to satisfy the tests.

1. Install SoapUI

   (Via GUI, or
   ```
   {downloaded package, e.g.}/Downloads/SoapUI-x64-5.2.1.sh -q -varfile {full-path-to-this-project}/SoapUI.varfile
   ```

2. Run the test suite:

   ```
   /usr/local/share/SoapUI-5.2.1/bin/testrunner.sh -PPORT=3000 ./Q3-Training-Tests-soapui-project.xml
   ```

   The SoapUI tests have properties that may be set to target your specific 
   implementation (as demonstrated above, by setting the PORT property.

   ```
   PORT: HTTP port to access REST services
   RS_HOST: HTTP host to access the Reservation REST service
   US_HOST: HTTP host to access the Reservation Update REST service (queue reader)
   ```

Quickstart
----------

1. Download Go - https://golang.org/dl/
2. Install Docker - https://docs.docker.com/docker-for-mac/
3. Install SoapUI - https://www.soapui.org/downloads/soapui.html
4. Install and start journal (all run from this project dir)

         export GOPATH=${HOME}/go
         cd ${HOME}/go
         mkdir -p $GOPATH/src/github.com/tdhite
         cd $GOPATH/src/github.com/tdhite
         git clone http://gerrit.eng.vmware.com:8080/q3-training-journal
         cd q3-training-journal
         make

         # If you have issues starting journal on a mac, follow this process instead
         docker run -it -v "$PWD":/go/src/github.com/tdhite/q3-training-journal -w /go/src/github.com/tdhite/q3-training-journal golang:1.6 make q3-training-journal
         docker build -t q3-training-journal --rm=true .

5. Build/start containers

        docker-compose up
        # or if you want to run it in the background
        docker-compse up -d

6. Access application at http://0.0.0.0/8090/app
