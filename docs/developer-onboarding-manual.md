## Developer Onboarding Manual

Welcome to the Lucy in the Loop developer community! This onboarding manual will help new developers (human or AI-assisted) set up their environment, understand the codebase, and start contributing effectively to the project. Whether you are an AI engineer, system architect, clinician with coding skills, or any contributor, this guide will orient you to develop within Lucy’s unique autonomous framework.

### Development Environment Setup

**Prerequisites:** Python 3.9+ (we use Python for core), Git, and recommended: a virtual environment tool (venv/conda). If you plan to modify front-end, Node.js for building UI (if we have a custom UI beyond simple HTML).

**1. Get the Code:** Fork the repository `quantumpipes/lucy-in-the-loop` to your GitHub (if you plan to submit contributions). Then clone your fork locally:

```bash
git clone https://github.com/YourUsername/lucy-in-the-loop.git
cd lucy-in-the-loop
```

This will create the project folder on your machine.

**2. Setup Virtual Environment:** (Optional but recommended to avoid dependency conflicts)

```bash
python3 -m venv venv
source venv/bin/activate   # or venv\Scripts\activate on Windows
```

**3. Install Dependencies:**
All requirements are in `requirements.txt`. Use:

```bash
pip install -r requirements.txt
```


This includes ML frameworks (PyTorch or similar), any web framework for the UI, etc. If you encounter issues (some packages may have platform-specific install steps, like pytorch or llama libraries), consult our documentation (“Developer Setup”) or ask in the forum.

**4. Install Optional Dev Tools:**
For a smoother development experience, install these extras:

* Code linters/formatters: We follow PEP 8, so using `flake8` or `pylint` is encouraged. We also have a config for `black` (auto-formatter) to keep style consistent.
* Testing frameworks: We use `pytest` for our automated tests. Install dev requirements:

```bash
pip install -r dev-requirements.txt  # if exists, for test and doc tools
```

(This might include `pytest`, coverage, etc.)

**5. Build/Run the Project (planned):**
Once application code is published, you will be able to run Lucy in development mode. Until then, contributions should focus on docs, policies, and processes.

**6. Running Tests (planned):**
Test suites will be provided alongside the application code. Our goal is high coverage; for now, CI validates documentation quality and links.

**7. Enable Autonomy (planned):** When agents are available, you may enable them in configuration. For now, agent-related references are design-only.

```yaml
autonomy:
  enabled: true
  dev_mode: true  # dev_mode might tell agents to not actually push to git, etc.
```

And run Lucy. Keep an eye on the console logs; you’ll see messages like “AI Coder Agent scanning issues...” which means the agent threads are running. For development, you might often run with autonomy off and test agents individually to avoid them interfering with your code changes in unpredictable ways.

### Understanding the Codebase

Lucy’s project is organized logically by components (following the modular spec):

* **`lucy/agents/`**: This package contains submodules for each agent or group of agents. For example, `lucy/agents/conversation.py`, `lucy/agents/therapy.py`, `lucy/agents/safety.py`, etc., and perhaps subpackages like `lucy/agents/dev/` for development agents, `lucy/agents/security/`, etc. Each agent class typically has methods like `process(input)` or `run_cycle()` depending on if they’re event-driven or looping. Read the docstring at the top of each agent module – we’ve documented their design and API.
* **`lucy/core/`**: Contains core orchestration logic. For instance, `orchestrator.py` (agent manager), `config.py` (loading configuration), `data_store.py` (interfaces to the encrypted local store), etc. The core is essentially the “glue” that connects agents. Understanding `orchestrator.py` is key – it shows how messages flow between agents, and how the main loop works (e.g., probably something like: on user input -> call conversation agent -> coordinate with other agents -> produce output).
* **`lucy/ui/`**: If the UI has its own code (HTML/JS or maybe a small Flask app), it’s here. For a web UI, we might have `lucy/ui/server.py` launching a local web server and `lucy/ui/templates/` with HTML files. The UI communicates with the core via API calls or direct Python function calls (depending on design). As a dev, if you change an agent’s interface, ensure the UI still calls it correctly.
* **`lucy/plugins/`**: Contains any default plugins (or examples). And the Plugin loader. If you add a new plugin, it would go here or in a separate project; but ensure our plugin manifest file (if any) is updated to load it.
* **`documentation/`**: (outside the package) – holds additional design docs like the ones referenced (e.g., `012-autonomous-agent-manifest.md` etc.). As a contributor, you should update relevant docs when you make notable changes (the Documentation Agent might do it, but in dev you often help it by writing human explanations).

**Code Style & Guidelines:**

* We use PEP 8 style (with a few project-specific tweaks). Use 4 spaces indent, and descriptive variable names. The Contribution Guidelines emphasized writing clear, self-documenting code. Comments are encouraged especially for complex logic. If you implement a tricky algorithm, write a summary of it. Our code has type hints gradually being added; please include type annotations in new code for clarity.
* **Docstrings:** We follow either Google style or reStructuredText in docstrings. Provide at least a one-line docstring for each function and class summarizing its purpose. For agents, list their main methods and what they do. The Documentation Agent often uses these docstrings to generate user docs, so it helps to keep them up-to-date.
* **Testing Your Changes:** Add or update tests for any new feature or bugfix. Our test suite is in `tests/`. Likely mirrored structure (e.g., `tests/test_conversation_agent.py`). We might have integration tests in `tests/integration/` as well, simulating user flows. After changes, run tests (including any relevant slow tests or scenario tests). Also run `pytest --runxfail` to see if you accidentally fixed something marked xfail.

**Running the Whole Autonomy Suite in Dev:**

If you want to see how dev agents commit code, etc., we have a simulated environment (probably a dummy git repo within the project or a dry-run mode). For example, AI Coder might by default not push to GitHub in dev mode but log the diff it *would* commit. You can examine that diff to verify it. If you actually want it to push, you might need to configure a GitHub token and set `AI_CODER_LIVE=true`. However, be cautious: letting it push to your fork could create spammy commits. We recommend in dev to keep it local. Or use a separate branch/repo to test live AI commits.

### Making Contributions

**Workflow:**

1. **Branching:** Create a new branch for your work:

   ```bash
   git checkout -b fix/memory-leak
   ```

   Use a descriptive name (feature/..., fix/..., docs/..., etc.).

2. **Coding & Testing:** Make your changes in the code. Use `pytest` frequently to ensure nothing breaks. If adding a feature, perhaps write tests first (TDD style) or at least simultaneously. If it's a bug fix, write a test that fails without your fix, then make it pass with the fix.

3. **Linting:** Run linters/formatters:

   ```bash
   flake8 lucy tests
   black lucy tests
   ```

   (Black autoformats; flake8 will point out issues black might not fix.) Also run `pylint` if set up. Documentation Agent or CI will double-check style in PRs, but it's good to do locally.

4. **Commit Changes:** Use clear commit messages. For example:

   ```
   git add lucy/agents/performance.py tests/test_performance_agent.py
   git commit -m "Optimize cache invalidation logic in Performance Agent (fixes #42)"
   ```

   If your commit is work-in-progress or references an issue, note it (e.g., "related to #123").

5. **Manual Testing:** Spin up Lucy with your changes and do some manual testing as a user to ensure everything flows as expected. This is especially important for UI changes or major logic changes. E.g., if you changed how the Safety Agent thresholds work, try conversing with Lucy about crisis topics to see if it responds appropriately.

6. **Documentation:** If you added a feature, update relevant documentation (README, or perhaps add a how-to in docs). Also, add an entry to `CHANGELOG.md` (if we maintain one) under "Unreleased" stating your change. The Documentation Agent might do it, but typically you'll add a summary like "- Fixed memory leak in caching (thanks @YourUsername)" in the changelog.

7. **Push to Fork:**

   ```bash
   git push origin fix/memory-leak
   ```

8. **Open Pull Request:** Go to GitHub and create a PR from your branch to `main` of the upstream. Fill out the template:

   * Describe the changes and why (link issues if it fixes something).
   * Mention any approach taken, and if you need feedback on certain implementation decisions.
   * Ensure the PR title is descriptive, e.g., "\[Fix] Memory leak in Performance Agent".

**PR Review Process:**

* Automated checks will run (CI might run tests, linters). Ensure they pass or address failures.
* Project maintainers or other contributors will review your PR. Be open to their feedback, which could request changes (like improving readability, adding a test, or altering approach).
* Discuss politely any suggestions; if you disagree, explain your reasoning but stay open. The goal is code that fits the project’s style and is robust.
* Once approvals are given and CI is green, a maintainer will merge your PR. If you have write access and the repo policy allows, do not self-merge unless trivial; usually wait for at least one other approval.

**Developing with AI Agents:**

Given Lucy's nature, you might consider using Lucy itself (or its dev agents) to help code! For instance, you could open an issue and see if AI Coder proposes a solution. In practice, during development you might run Lucy and use the **Metrics & Dev Dashboard** (if available) to watch agent metrics (like autonomy rate, errors). There’s also likely a CLI to query agent status (`lucy-admin status` as shown: printing autonomy rate, escalation count, etc.). This can help in debugging: e.g., `lucy-admin health-check` gives you a quick overview of all agents' health.

**Tips:**

* Start by tackling a small issue or adding a minor feature to get familiar with the codebase.
* Read through some existing code to see the patterns. For example, how do we handle logging? (We probably have a centralized logger that each agent uses, with context in logs of which agent is speaking).
* If working on AI/ML parts: maybe the conversation model code is not fully in this repo (maybe loaded from a model file). But any logic around it (like prompt handling, safety filtering) is here. Understand how the model is invoked and where to integrate changes (like if adjusting how we prompt the model, that might be in conversation agent).
* Performance: When adding features, be mindful of resource use. On a local system, we can’t bloat memory or CPU too much. E.g., if you add a new agent, ensure it sleeps or waits appropriately to not hog CPU. Many agents likely run asynchronously or on timers. Use efficient algorithms (the Refactoring Agent might catch inefficiencies, but it's good dev practice to consider upfront).
* **AI Ethics & Safety:** Any changes should keep ethics in mind. If you modify something that could affect outputs or user interactions, consider potential misuse or harm. E.g., if you adjust how content filtering works, test that it still blocks what it should. If you add a new prompt, ensure it doesn't inadvertently bias the AI.

**Getting Help:**

* We have a developer chat/forum for questions. Don’t hesitate to ask if you’re unsure why something is done a certain way or how to approach a problem. The community is friendly and would rather you ask than struggle or make an avoidable mistake.
* Check existing issues/PRs for hints—maybe someone attempted similar changes before, or there's an open issue discussing the design.
* Our documentation (particularly the Autonomous Agent Manifest and design specs) can give context on the intent behind modules. If something in code doesn’t match the docs, note it—it could be a doc lag or a bug.

**Advanced Topics:**

* *Optimization:* If you want to optimize model performance (e.g., converting to use ONNX or adding a GPU acceleration), this is welcome but please coordinate via an issue first, as these can be complex changes. We value optimization given the local constraint, but it must be stable across platforms.
* *Security Development:* If working on the Security or Privacy agent, be extra cautious and test thoroughly. Those have heavy responsibility.
* *Clinician Input:* We also encourage contributions from clinicians. If you're one and have code skills, perhaps you want to adjust how a therapy protocol runs. We welcome that insight, and we’ll ensure any clinical logic changes are reviewed by others with domain knowledge for safety.

**Continuous Improvement Culture:**

We rely on contributions to evolve Lucy. Even as AI agents handle more, human devs are crucial to guide the vision, handle complex changes, and set constraints. You’ll notice sometimes the AI Dev Agents might open pull requests too. Treat them as you would human contributions: review their changes (they’ll often tag a human for review anyway). This collaboration between human and AI developers is unique in our project. Embrace it – for example, you could assign a tedious refactor to the AI (via an issue) and focus on creative tasks.

We maintain an **Ethics & Code of Conduct in Dev**: Always incorporate privacy and ethics in your code (like not logging sensitive data unnecessarily, etc.). And treat fellow contributors with respect and patience, as mentioned.

### Running Lucy in Development vs Production

* **Dev Mode** might include verbose logging, debug endpoints (maybe a `/debug` HTTP route showing internal state), and disabled real autonomous actions (like AI Coder might not auto-merge without a flag).
* **Production Mode** is what end-users run: quieter logs, everything streamlined, and autonomous actions fully enabled with safeguards.

As a dev, test in both where applicable. For instance, test that your feature works with autonomy off (manual path) and on (ensuring it doesn’t break automation).

### Optimization and Deployment Considerations

If you contribute changes that affect performance or memory, try to test on a lower-end machine (if possible simulate 8GB RAM, no GPU environment) to ensure Lucy still runs within limits.

For deployment packaging (if we distribute Lucy as an app or container), be aware how your changes affect that. E.g., adding a large dependency could bloat an installer – is it worth it? Discuss such additions with maintainers.

We aim to support Windows, Linux, Mac. If you’re on one OS, at least check that your code doesn’t use OS-specific paths or commands. Our CI likely tests on multiple OSes.

### Conclusion

We’re excited to have you contribute to Lucy in the Loop. This project is pushing boundaries in AI autonomy and ethical tech, and as a developer, you’re part of this pioneering effort. Start small, ask questions, and gradually you’ll become familiar with the system’s intricacies. We also encourage you to interact with Lucy as a user – that perspective helps to understand what to improve.

Remember to always run `lucy --health-check` to verify all agents are healthy after your changes, and run our full test suite + linting before pushing commits (our CI will do it too, but it’s good practice to catch issues early).

Happy coding, and thanks for helping build Lucy in the Loop into a world-class AI companion!

*(If any step in this onboarding is unclear or you encounter setup issues, please let us know so we can improve the documentation for the next developer.)*
