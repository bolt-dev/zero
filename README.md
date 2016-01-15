Code Layout
===========

JSMime is a MIME parsing and composition library that is written completely in
JavaScript using ES6 functionality and WebAPIs (where such APIs exist). There
are a few features for which a standardized WebAPI does not exist; for these,
external JavaScript libraries are used.

The MIME parser consists of three logical phases of translation:

1. Build the MIME (and pseudo-MIME) tree.
2. Convert the MIME tree into a list of body parts and attachments.
3. Use the result to drive a displayed version of the message.

The first stage is located in `mimeparser.js`. The latter stages have yet to be
implemented.

Dependencies
============

This code depends on the following ES6 features and Web APIs:
* ES6 generators
* ES6 Map and Set
* ES6 @@iterator support (especially for Map and Set)
* ES6 let
* ES6 let-destructuring
* ES6 const
* Typed arrays (predominantly Uint8Array)
* btoa, atob (found on global Windows or WorkerScopes)
* TextDecoder

Developments
============
```
npm install -g mocha # For running mocha tests
npm install -g http-server # Installing the http-server for firefox test
http-server # At the jsmime root directory

npm install -g gulp # Installing gulp for mocha test with node

gulp test #Running all the tests
npm run mocha -- test\test_header.js #Used for running specific test case

gulp bundle # Creating the dist\jsmime.js that could be able used in browser
gulp coverage # Viewing the running result
gulp watch # Watch the file changes & generating the dist\jsmime.js automatically
```

Versions and API stability
==========================

As APIs require some use and experimentation to get a feel for what works best,
the APIs may change between successive version updates as uses indicate
substandard or error-prone APIs. Therefore, there will be no guarantee of API
stability until version 1.0 is released.

This code is being initially developed as an effort to replace the MIME library
within Thunderbird. New versions will be released as needed to bring new support
into the Thunderbird codebase; version 1.0 will correspond to the version where
feature-parity with the old MIME library is reached. The set of features which
will be added before 1.0 are the following:
* S/MIME encryption and decryption
* PGP encryption and decryption
* IMAP parts-on-demand support
* Support for text/plain to HTML conversion for display
* Support for HTML downgrading and sanitization for display
* Support for all major multipart types
* Ability to convert HTML documents to text/plain and multipart/related
* Support for building outgoing messages
* Support for IDN and EAI
* yEnc and uuencode decoding support
* Support for date and Message-ID/References-like headers

Other features than these may be added before version 1.0 is released (most
notably TNEF decoding support), but they are not considered necessary to release
a version 1.0.
