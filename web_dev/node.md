# node

## event loop
- single threaded
- non-blocking
- keep running as long as one listener registered
- execute
  - execute dued timer callbacks
    - setTimeout, setInterval
  - execute I/O callbacks or defer
  - poll
    - retrieve new I/O events
    - execute their callbacks
  - check
    - setImmediate
  - close cbs

## streams & buffers
- process chunks of data in buffer
- allows to interact with data early


## express