Modal Images are defined programmatically rather than via traditional Dockerfiles, and modern DevSecOps practices dictate that sensitive credentials must be injected securely at runtime. A machine learning pipeline requires the `transformers` library and an API key to download restricted models from an external repository.

You need to create a Modal Image definition that installs `transformers` via pip and attach a Modal Secret named `huggingface-token` to a deployed function requesting a single A10G GPU.

**Constraints:**
- Use the modern string shortcode syntax for the GPU definition (e.g., `gpu="A10G"`), do not use the deprecated class-based instantiation.
- Do not embed the API key directly in the Python code or Image definition.