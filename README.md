# Postman collections for Nasirtms/Postman

This repository stores Postman collections, environments and related assets for APIs you want to share, test, and run in CI.

Why this repo exists
- Single place to keep Postman collections and environment files under version control.
- Run automated API tests via GitHub Actions (Newman).
- Provide clear import and contribution instructions.

Repository layout (recommended)
- /collections/                -> Postman collections (.json)
- /environments/               -> Postman environment files (.postman_environment.json or .json)
- /examples/                   -> example requests, sample payloads or response samples
- /.github/workflows/          -> CI workflows that run Newman
- README.md, CONTRIBUTING.md, .gitignore, LICENSE

How to import into Postman
1. Open Postman -> File -> Import -> Choose Files -> select the JSON in `collections/` or `environments/`.
2. Or drag and drop the JSON files into Postman.

Local testing with Newman
1. Install newman:
   - npm: npm install -g newman
2. Run a collection:
   - newman run collections/your-collection.postman_collection.json
3. If you need environment variables:
   - newman run collections/your-collection.postman_collection.json -e environments/dev.postman_environment.json
4. To pass secrets from environment variables (avoid committing secrets):
   - newman run collections/your-collection.postman_collection.json --env-var "API_KEY=$API_KEY"

CI (GitHub Actions) notes
- The repo includes an example workflow that installs newman and runs collections on push/PR.
- Do NOT commit real secrets to repository environment files. Use GitHub repository secrets and the workflow will inject them at runtime.

Secrets / sensitive data
- Never commit API keys, tokens, or secrets. Instead:
  - Keep a sanitized environment file (no secrets) in `environments/` and store secret values in GitHub repository secrets.
  - Or keep environment files out of repo and share privately.
- Add `*.postman_environment.json` or environment filenames to `.gitignore` if they contain secrets.

Naming conventions
- collections/{api-name}.postman_collection.json
- environments/{env-name}.postman_environment.json
- Use semantic naming and include a version field in collection documentation when relevant.

Suggested next steps
- Add a license (MIT) if you want others to reuse the collections.
- If you want automation, I can push the example workflow and README into your repo.
- I can convert exported Postman collections into the structured folder layout for you.
