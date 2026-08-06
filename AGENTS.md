# Production Colab release rules

- Keep this repository public and use `main` as the default branch.
- Use the existing SmartCoder hospital services. Do not create a separate service, port, or runtime for these notebooks.
- Use synthetic clinical text only. Never add real patient data, personal identifiers, saved API responses, or executed cell output.
- Every request must be raw-note-only and must verify polishing, three NER votes, terminology linking, `TXT_NER` sources, SNOMED membership, callback GET consistency, and Colab CORS.
- The CSH notebook may contain only its deliberately public, replaceable Colab access token. Keep internal maintenance credentials out of this repository.
- Other hospitals must obtain credentials only through `getpass`; do not read credential environment variables or commit their keys.
- Each notebook must call exactly one configured API base URL and one complete clinical workflow. Never switch services, URLs, credential sources, or processing paths after an error.
- Read every required response field by its exact key and validate its type and value. Missing or malformed fields must stop execution immediately; do not substitute empty collections or default values.
- Keep stable notebook URLs on public `main` and use filenames ending in `_smartcoder_api.ipynb`.
- Record verification status truthfully. Pending or unavailable services must stop explicitly and must not be marked as passed.
- Before release, verify anonymous GitHub access, anonymous notebook download, zero saved outputs, and the CSH end-to-end flow from the published notebook.
