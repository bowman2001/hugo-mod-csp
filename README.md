# Hugo module to generate a server header

The module is in alpha stage and can only generate the file `_header` for Netlify including a site wide CSP and other security settings.

A content security policy doesn’t necessarily need a hugo module. We may well write one without it. But the syntax is complicated enough to expect typing errors and other mistakes which could undermine the result and the intended security. This module checks the syntax of all entries to prevent a faulty header.

## Syntax source & check

- The syntax for a content security policy (CSP) [is documented here][csp] for example.

- We can check our CSP as soon as its attached to a website [here](https://observatory.mozilla.org/)

## Goal

CSP is a second line of defense against attacks. The task is always the same: Advising the web-server to send a header with our specific content restrictions. 

### Different output formats

There are different ways to accomplish this task and this module could be able to generate different formats.

### Validation

- The syntax of all keys and special values gets checked against the official syntax elements.  (nonce-* and sha-* are still missing)

- URLs and pure schemes get parsed by Hugo’s urls.Parse, which is based on the standard Golang method.

## Prerequisites

This module expects a CSP section in the Hugo project parameters.

## Output

- One output format is a `_header` file. An elegant way to generate the header without generating additional HTML. Netlify can process this file.

- The second implementation should be a meta tag for the HTML header. This is less efficient, because we need additional HTML code. And a few rules don’t have any effect as meta tags. Meta tags have only one advantage: They work on all servers without access to the configuration of the web server.  

[csp]: https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP "MDN"

## Configuration syntax (TODO)
