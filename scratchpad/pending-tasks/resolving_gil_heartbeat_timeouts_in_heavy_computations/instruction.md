The Modal host monitors container health via a continuous heartbeat thread. Synchronous C-extension code (common in traditional data processing) that refuses to yield the Global Interpreter Lock (GIL) for extended periods will starve this thread, causing the platform to assume the container is dead and forcibly terminate it.

You need to refactor a computationally heavy, blocking Python function so that the core workload executes inside a spawned subprocess, allowing the main thread's heartbeat to continue pulsing to the host.

**Constraints:**
- Do not modify the underlying C-extension logic or artificially chunk the execution time.
- The parent Python function must wait for the subprocess to complete and accurately retrieve its standard output and exit status.