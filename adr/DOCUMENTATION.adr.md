# Documentation

## Decision
The documentation of **Kraft**SQL contains:

**User Documentation**
- a central "User Guide" for all parts of **Kraft**SQL
  - This includes
    - "Getting Started"
    - architectural concepts
    - further guides about specific topics (e.g. testing)
    - a list of official connectors and their detailed documentation as well as a list of known community connectors
    - ...
  - It is written in the wiki of a central 'documentation' repository.
- the project's JavaDoc as a structured reference of its content
  - It is served as Github Pages of the 'documentation' repository.
  - It is versioned together with the **Kraft**SQL version.
- a `README.md` in each repository with minimal documentation
  - These `README.md`s link to the actual, central documentation.
- the **KRAFT**SQL organization's profile as landing page ('.github' repository), linking to the actual, central documentation

**Additional Developer Documentation**
- these Architecture Decision Records in this repository
- a `DEVELOPMENT.md` in each repository describing the development setup to work on it
- a central `CONTRIBUTING.md` in the '.github' repository describing the development workflow and how to contribute
  - This is linked from each repository.

### Explanation 
This ADR describes two aspects:
1. the content and structure of the documentation:
   This is a collection of the currently known requirements what to document. More documentation is possible.
3. the implementation of the documentation and tools used for it:
   These were chosen to be freely available, close to Github as the development platform and with minimal further tooling necessary, while fulfilling the requirements of what and how to document.

### Comparison of alternatives
There wasn't a real search for alternatives.
Instead, the available tooling of Github, i.e. Markdown files in the repositories, pages and wikis, was briefly evaluated, to cause minimal overhead for the documentation.
The solution is a combination of these tools to implement each part of the documentation.
