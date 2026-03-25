Autonomous AI agents often need to execute dynamically generated, potentially untrusted code in a secure, isolated environment. Modal's Sandbox feature allows programmatic container generation for this exact use case, but mounting volumes to GPU sandboxes currently triggers a documented bug causing a silent background crash.

You need to programmatically provision an ephemeral Modal Sandbox with a single T4 GPU attached to execute an untrusted Python script string securely.

**Constraints:**
- Do NOT mount any `modal.Volume` to the Sandbox to avoid triggering the known `NotFoundError` silent crash bug.
- Ensure the programmatic execution captures and returns the standard output (stdout) of the script to the parent application.