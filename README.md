# Calypso Networks Association Terminal API documentation

[![License](https://img.shields.io/badge/License-EPL_2.0-red.svg)](https://opensource.org/licenses/EPL-2.0)

Central repository for design documentation of all **Calypso Terminal API** libraries, including **UML diagrams** and conception documents.

## Repository Structure

This repository uses two main branches:
- `main`: Contains the repository configuration and workflows
- `gh-pages`: Contains the actual documentation and Jekyll configuration, published at [https://docs.terminal-api.calypsonet.org/](https://docs.terminal-api.calypsonet.org/)

## Managing Documentation Sources

### Adding a New Library Documentation

To add documentation for a new library:

```bash
# Switch to `gh-pages` branch
git checkout gh-pages

# Add the submodule pointing to the doc branch
git submodule add -b doc https://github.com/calypsonet/[library-name].git [library-name]

# Commit the changes
git add .
git commit -m "feat: add documentation for [library-name]"
git push origin gh-pages
```

### Removing a Library Documentation

To remove documentation for a library:

```bash
# Switch to `gh-pages` branch
git checkout gh-pages

# Remove the submodule
git submodule deinit -f [library-name]
rm -rf .git/modules/[library-name]
git rm -f [library-name]

# Commit the changes
git commit -m "feat: remove documentation for [library-name]"
git push origin gh-pages
```

## Automatic Updates

This repository includes a GitHub Action that automatically updates all submodules to their latest commits. The action:

- Runs on manual trigger, repository dispatch event, or push to gh-pages
- Updates all submodules recursively
- Commits and pushes changes if updates are detected
- Uses a dedicated bot account for commits

You can view the action workflow in [`/.github/workflows/update-submodules.yml`](https://github.com/calypsonet/terminal-api-doc/blob/main/.github/workflows/update-submodules.yml).

## Contributing

Please read our [contribution guidelines](https://terminal-api.calypsonet.org/community/contributing/) before submitting any changes.

## License

This project is licensed under the Eclipse Public License v. 2.0. See [LICENSE](LICENSE) for details.
