## Contribution Guidelines

*Thank you for your interest in contributing to Lucy in the Loop!* We welcome contributions from developers, mental health professionals, researchers, and enthusiasts who share our vision of an ethical, privacy-focused AI companion. The following guidelines will help you get started as a contributor and outline the standards for contributing code, documentation, or other improvements.

### How to Contribute

We encourage a wide variety of contributions, including:

* **🌟 New Feature Ideas:** If you have an idea for an enhancement or a new capability, feel free to suggest it. You can start a discussion or open an issue describing the feature.
* **🐛 Bug Reports:** If you find a bug or security vulnerability, please report it through the issue tracker with details to help us reproduce and understand the problem.
* **🛠 Code Contributions:** You can fix bugs, implement new features, improve performance, or refactor existing code. All code contributions are welcome as long as they align with the project’s goals and standards.
* **📝 Documentation:** Improving documentation, writing tutorials, or translating docs into other languages are valuable contributions. Clear docs help everyone.
* **✅ Testing:** You can contribute by writing test cases, performing manual testing, or reviewing others’ code changes for potential issues. Ensuring Lucy’s reliability across scenarios is a great way to help.

No contribution is too small – even fixing typos or answering questions in the forum is appreciated!

### Ground Rules

Before you start, a few important ground rules:

* **Be Respectful and Ethical:** All contributors must adhere to our Code of Conduct (see above). Respect user privacy and follow our ethics guidelines in all your contributions. For example, code should not introduce biases or privacy risks.
* **Discussion and Consensus:** For significant changes, please discuss your idea first (via GitHub issues or discussions) to gather feedback and ensure it aligns with the project roadmap. This helps avoid duplicate work and design misalignment.
* **License Agreement:** By contributing, you agree that your contributions will be licensed under the same Apache 2.0 License as the project. This ensures we can distribute your code within Lucy in the Loop.

## Developer Certificate of Origin (DCO)

We use the DCO 1.1. To certify the originality of your contribution, add this
line to each commit message:

Signed-off-by: Your Name <email@example.com>

Use `git commit -s` to add it automatically. See `DCO.md` for details.

### Development Workflow

To contribute code or documentation, please follow this workflow:

1. **Fork the Repository:** Click “Fork” on the GitHub repo (quantumpipes/lucy-in-the-loop) to create your own copy. Then clone your fork locally:

   ```bash
   git clone https://github.com/YourUsername/lucy-in-the-loop.git  
   cd lucy-in-the-loop
   ```


2\. **Create a Branch:** Create a new git branch for your work. Use a descriptive name that reflects the change, for example `feature/add-mood-tracker` or `fix/memory-leak`.

```bash
git checkout -b feature/add-mood-tracker
```


Ensure each separate feature or fix goes in its own branch. This makes it easier to review and merge.
3\. **Implement Your Changes:** Make code or documentation changes on your branch. Follow the project’s coding standards: we use **Python PEP 8** style for Python code (use consistent formatting and lint your code). Include comments for any complex logic, and make sure functions and classes are documented clearly. If you’re fixing a bug or adding a feature, try to write or update tests to cover it (our goal is high test coverage for all functionality).
4\. **Commit Changes:** Commit your work in logical chunks with clear commit messages. A good commit message briefly describes *what* and *why* (e.g., “Fix crash in Safety Agent when message is empty”). Avoid large monolithic commits – smaller incremental commits are easier to review.

```bash
git add .
git commit -m "Add mood tracker feature with daily prompt (resolves #123)"
git push origin feature/add-mood-tracker
```


(Replace “feature/add-mood-tracker” with your branch name.) Push your branch to your GitHub fork.
5\. **Open a Pull Request:** Go to your fork on GitHub and click “Compare & Pull Request.” Fill out the PR template, describing your changes in detail and linking any relevant issue numbers (e.g., “Closes #123”). Explain **why** the change is beneficial and any new dependencies or potential impacts it introduces. Mark the PR as draft if it’s not ready for full review.
6\. **Code Review:** Project maintainers (or automated agents) will review your pull request. Please be open to feedback and make revisions if requested. Code review is a positive process to improve both the project and your contribution. You may be asked to adjust style, add tests, or clarify design decisions.
7\. **Merge:** Once your PR is approved by maintainers (and passes continuous integration tests), it will be merged into the main codebase. Congratulations – you’ve contributed to Lucy in the Loop! 🎉  (If you have write access and are merging yourself, ensure at least one other person reviewed, and do not self-merge without review except for trivial fixes.)

### Documentation Contributions

For contributions to documentation or non-code content, a similar process applies:

* **Clarity and Accessibility:** Write in clear, easy-to-understand English. Our docs aim to be accessible to a broad audience (developers, clinicians, general users), so avoid unnecessary jargon and define terms when first used.
* **Structure:** Use Markdown formatting consistently. Follow the style of existing docs for headings, bullet points, etc., to maintain uniformity. If adding a new document, consider where it fits in the documentation hierarchy.
* **Examples and Diagrams:** Provide examples (code snippets, command usage, screenshots/diagrams) where helpful. For instance, if you’re writing a tutorial on configuring Lucy’s privacy settings, include sample config excerpts. Visual aids like architecture diagrams are welcome (ensure they are clear and have alt text for accessibility).
* **Translation:** If contributing a translation, ensure you are fluent in the target language and consider cultural context for mental health terminology. Possibly coordinate with others if multiple translators are involved.

As with code, you can propose doc changes via pull requests. Documentation changes also go through review to ensure accuracy and coherence.

### Community and Support

Aside from direct contributions, you can also help by engaging with the community:

* Answer user questions in the GitHub Discussions or forums if you know the solution.
* Suggest design improvements or point out areas of code that could use refactoring (the AI Refactoring Agent appreciates human perspective too!).
* Help triage issues – label bugs, confirm if you can reproduce issues on your setup, or close issues that are resolved.

All contributors should also be mindful of our **Ethical Standards**: always prioritize user well-being, privacy, and transparency in any contribution. Lucy in the Loop is a mission-driven project, and we value contributions that uphold our commitment to ethical AI.

Thank you for contributing your time and expertise to Lucy in the Loop! Together, we’re advancing the future of accessible, ethical mental health care, one commit at a time.
