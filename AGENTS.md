# Public demo release rules

- Keep this repository public and use `main` as the default branch.
- Keep the Colab notebook zero-input: a visitor must be able to choose **Run all** without supplying credentials or environment variables.
- Never publish a production credential. The notebook may contain only a deliberately public, replaceable demo token backed by an isolated, rate-limited demo service.
- Use synthetic clinical text only. Never add real patient data, personal identifiers, saved API responses, or executed cell output.
- Keep the stable Colab URL on the public `main` branch.
- Before release, verify anonymous GitHub access, anonymous notebook download, POST/GET acceptance with the same request ID, non-empty coding output, and Colab CORS.

