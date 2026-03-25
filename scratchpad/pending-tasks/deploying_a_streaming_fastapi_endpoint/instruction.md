Real-time AI applications rely on Server-Sent Events (SSE) to stream inference tokens to the client, which significantly reduces perceived latency. Modal natively supports streaming using FastAPI's `StreamingResponse` class wrapped via its updated SDK decorators.

You need to deploy a web endpoint using the `@modal.fastapi_endpoint` decorator that yields a synchronous generator of byte strings with the `text/event-stream` MIME type. 

**Constraints:**
- Do not use the deprecated `@modal.web_endpoint` decorator.
- The endpoint must successfully simulate a streaming response by yielding sequential chunks of a predefined text string.