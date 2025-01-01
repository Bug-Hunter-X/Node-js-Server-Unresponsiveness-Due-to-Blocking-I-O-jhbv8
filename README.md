# Node.js Server Unresponsiveness Due to Blocking I/O

This repository demonstrates a common issue in Node.js where a long-running synchronous operation in the request handler blocks the event loop, causing the server to become unresponsive.  The bug is that a 5-second CPU-bound loop in the request handler prevents any other requests from being processed.

## Bug

The `bug.js` file contains a simple HTTP server with a request handler that performs a long-running synchronous operation. This blocks the event loop, preventing the server from handling further requests.  This results in the server appearing unresponsive to clients.

## Solution

The `bugSolution.js` file demonstrates the solution.  Asynchronous operations using `setTimeout` are used to avoid blocking the event loop.  Even with a long running task, the server will remain responsive.

## How to run

1. Clone this repository.
2. Navigate to the repository directory.
3. Run `node bug.js` to see the unresponsive behavior.
4. Run `node bugSolution.js` to see the corrected, responsive server.