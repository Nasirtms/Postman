# Contributing

Thanks for contributing! A few guidelines to keep collections organized and safe.

Add or update a collection
- Place the exported collection JSON into `collections/` with a descriptive filename:
  - Example: `collections/users-service.postman_collection.json`
- If you add environment files, sanitize them (remove secret tokens) or keep private copies outside the repo.
- Add a short description in the PR describing what the collection covers and any preconditions.

Testing
- Add Newman tests or pre-request scripts/assertions inside the Postman collection.
- CI will run `collections/your-collection.postman_collection.json` by default; update `.github/workflows/newman.yml` if you introduce new paths.

Secrets
- Do not commit secrets. Use GitHub repository secrets and the CI workflow to inject them at runtime (see README).

Style
- Keep collection names lowercase and hyphen-separated.
- Include a version field or tag the collection filename with v1, v2 if you need to track breaking changes.

Questions
- Open an issue or mention maintainers in the PR for anything that needs discussion.