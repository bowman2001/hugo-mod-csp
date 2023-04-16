# Hugo module to generate the header with the content security policy

## Syntax source & check

- The syntax for a content security policy (CSP) [is documented here][csp] for example.

- We can check our CSP [here](https://observatory.mozilla.org/)

## Goal

The task is always the same: Advising the web-server to send a header with our specific content restrictions.

### Different output formats

But there are different ways to accomplish this task and this module should be able to generate different formats.

### Validation

A content security policy doesn’t necessarily need a hugo module and we may well write one without it. But the syntax is complicated enough to expect typing errors and other mistakes. This module checks the syntax of all entries to prevent a faulty header.

## Prerequisites

This module expects a CSP section in the Hugo project parameters and the desired output format.

- The first implemented output format will be a `_header` file. An elegant way to generate the header without generating additional HTML. Netlify can process this file.

- The second implementation should be a meta tag for the HTML header. This is less efficient, because we need additional HTML code, but it works on all servers. But a few rules don’t have any effect as meta tag.  

[csp]: https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP "MDN"
