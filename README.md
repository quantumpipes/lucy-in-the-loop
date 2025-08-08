## README – Mission, Vision, and Usage Guide

Note on repository status: This repository currently contains legal, governance, and design documentation. The application code has not yet been published. Any references to commands, ports, dashboards, or binaries describe planned functionality for the initial MVP and are not runnable today.

### Mission & Vision

Lucy in the Loop’s mission is to **democratize mental healthcare** by providing a world-class AI mental health companion that is secure, autonomous, and entirely under the user’s control. Our vision is a future where mental health support is accessible to anyone, anywhere, without sacrificing privacy or quality of care. To achieve this, Lucy is built as a **fully offline, self-evolving intelligence** that resides on your device and continuously improves itself. It operates with a groundbreaking *99% autonomous / 1% human* governance model, meaning nearly all routine operations are handled by AI, with human input reserved only for critical ethical and safety decisions. In short, **Lucy in the Loop** is *“the world's first fully autonomous mental health AI system”* – a living software that writes its own code, heals itself, and adapts to each user while remaining privacy-first.

### Manifesto

For our moonshot vision and the guardrails that keep it safe, see the project manifesto: [MANIFESTO.md](./MANIFESTO.md). It lays out first principles (privacy, safety, transparency, equity), our 99/1 autonomy model with human oversight, and commitments to users, clinicians, developers, and society.

### Key Features and Goals

Lucy in the Loop is designed with the following core features and goals:

* **Offline AI Operation** – Runs entirely on local hardware with no cloud dependency, ensuring data never leaves the user’s device. This local-first design supports confidentiality and HIPAA/GDPR‑aligned handling; formal compliance depends on deployment and configuration.
* **Privacy & Security Compliance** – Enforces strict data privacy (HIPAA, GDPR) and data sovereignty through on-device storage and encryption. Users have full control over their data.
* **Therapeutic Excellence** – Provides evidence-based therapeutic techniques including Cognitive Behavioral Therapy (CBT), Dialectical Behavior Therapy (DBT), Acceptance and Commitment Therapy (ACT), trauma-informed care, and more. Interventions are informed by the latest clinical research and tailored to individual needs.
* **Personalized, Adaptive Support** – Continuously learns and adapts to the user’s patterns. Each installation optimizes itself for the specific hardware and personal usage, achieving up to 10× performance improvements by tuning to the device. It personalizes coaching and support based on what works best for the user.
* **Self-Healing & Autonomous Maintenance** – Detects and fixes software issues proactively without any internet connection. Lucy’s agents can predict failures and resolve them automatically, keeping the system running smoothly 24/7.
* **Explainable & Transparent AI** – Every suggestion and action comes with an explanation. Lucy is designed to clearly explain its therapeutic recommendations in understandable terms, fostering trust through transparency. All autonomous decisions are logged for review (see *Transparent Autonomy Policy*).
* **Open Source & Community-Driven** – The project is fully open source (Apache 2.0) and welcomes community involvement. Development decisions and model updates occur in the open, inviting collaboration from developers, clinicians, and users worldwide. Lucy even has AI agents that handle documentation and community support to keep information flowing openly.



These features support the overarching goal: **a private, ethical, and ever-improving AI companion** that empowers users to improve mental well-being and performance without sacrificing control or confidentiality.

### Architecture Overview

At its core, Lucy in the Loop runs a **multi-agent architecture** – a collection of specialized AI agents that work together to deliver mental health support and maintain the system. This modular “society of AIs” allows Lucy to handle many tasks in parallel and adapt over time. Key components of this architecture include:

* **Core Therapeutic Agents** – These are the user-facing minds of Lucy. For example, a **Conversation Agent** conducts empathetic dialog with the user, while a **Therapeutic Agent** applies CBT/DBT techniques with clinical precision. A **Safety Agent** monitors for any risk of crisis or self-harm in real time, ready to intervene if needed, and a **Personalization Agent** learns the user’s unique preferences to tailor the experience. Together, they ensure interactions are supportive, safe, and personalized.
* **Autonomous Development & Maintenance Agents** – Behind the scenes, Lucy has agents like the **AI Coder** that reads GitHub issues and writes code to improve the system, a **Testing Agent** that creates and runs test suites (>95% coverage), and a **Documentation Agent** that keeps all guides and API docs up-to-date. These agents allow Lucy to literally improve and document itself over time without needing constant human engineering input.
* **Self-Healing Operations Agents** – Agents such as the **Predictive Maintenance** module watch for any system anomalies or performance drops and proactively fix them. A **Remediation (Self-Healing) Agent** can execute recovery workflows if something goes wrong, and a **Performance Optimizer** tunes system resources for optimal speed. There’s even a **Chaos Agent** that intentionally injects test failures to ensure Lucy is resilient under stress.
* **Security & Compliance Agents** – Lucy’s architecture includes a dedicated **Security Agent** that hunts for vulnerabilities or malware-like behaviors and generates instant patches (even for zero-day threats). A **Compliance Validator** agent continuously checks that the system conforms to privacy laws (HIPAA, GDPR, etc.) and internal ethical policies. Additionally, an **Encryption Manager** handles cryptographic functions like key rotation and data encryption to enforce data sovereignty.
* **Research & Innovation Agents** – A **Literature Monitor** agent scans mental health research (journals, PubMed) to keep Lucy’s knowledge up-to-date. A **Protocol Optimizer** updates therapy techniques based on the latest evidence, and an **Experiment Designer** agent runs A/B tests to validate new approaches. There’s also a **Knowledge Graph Builder** that maintains a rich network of mental health concepts, which Lucy uses to reason about user problems in a nuanced way.
* **Community & Support Agents** – Lucy even helps maintain its own community. An **Issue Triager** agent automatically processes user feedback or bug reports, a **Support Agent** drafts helpful responses to user questions, a **Sentiment Analyzer** gauges community well-being, and a **Feature Prioritizer** sorts feature requests by impact. These ensure that the project’s users and contributors are heard and assisted promptly, 24/7.
* **Privacy & Data Governance** – A set of agents focuses on data privacy. For instance, a **Consent Manager** gives fine-grained control over what data Lucy uses, a **Data Minimizer** ensures only minimal necessary data is kept, a **Deletion Scheduler** purges old data after set periods, and an **Access Controller** enforces a zero-trust security model for any access to data. These mechanisms mean that privacy isn’t just a policy – it’s actively maintained by the AI itself.

All these agents communicate and collaborate under a unifying orchestrator to form Lucy’s intelligence. This architecture is **fully modular** – each agent is a pluggable component, allowing the system to extend or modify capabilities easily (see *Modular Agent Design Spec* for details). The design also embraces the **99/1 Principle**: **approximately 99% of operations are handled autonomously by AI**, whereas **1% require human or community oversight** in clearly defined domains. Routine tasks like code updates, bug fixes, optimizations, and user support are automated, while critical decisions affecting ethics, safety, privacy, or major changes are funneled to human governance boards or maintainers. This structure enables unprecedented scalability and evolution speed, while still keeping a human “in the loop” for the most sensitive aspects of the project’s direction and user safety.

*(For a deep dive into each agent and the orchestration mechanism, see the **Modular Agent Design Spec** section of this blueprint.)*

### Planned Installation & Usage (not yet available)

> The following steps are illustrative and will become executable once the application code is published.

**System Requirements:** To run Lucy in the Loop, your system should meet the following minimum requirements:

* **CPU:** 8 physical cores (modern 64-bit processor)
* **Memory:** 16 GB RAM (8 GB RAM is possible if using 4-bit quantized models to reduce memory usage)
* **GPU:** *Optional but recommended.* A CUDA-compatible GPU (e.g. NVIDIA RTX 3060 or better) or Apple M-series neural engine can significantly accelerate AI processing. Lucy will use the GPU if available for heavy neural network computations.
* **Disk:** Sufficient storage for models and data (exact needs depend on model sizes, but \~10 GB free is a safe starting point).
* **OS:** Windows, Linux, or macOS are supported platforms.
* **Mobile:** Experimental support for mobile devices (iOS/Android) with WebGPU or Metal support and ≥6 GB RAM is available, allowing Lucy to run on high-end phones or tablets in a pared-down mode.

**Installation Steps:** (for developers and advanced users familiar with command line)

1. **Clone the Repository:** Download the latest code from GitHub.

   ```sh
   git clone https://github.com/quantumpipes/lucy-in-the-loop.git
   cd lucy-in-the-loop
   ```
2. **Install Dependencies:** Lucy’s core is written in Python, so install the required Python packages (it is recommended to use a virtual environment).

   ```sh
   pip install -r requirements.txt
   ```

   This will install all necessary libraries (machine learning frameworks, etc.).
3. **Run Lucy:** Start the application.

   ```sh
   python run_lucy.py
   ```

   This launches Lucy in standard mode on your machine.
4. **Access the Interface:** Once running, open your web browser and navigate to **`http://localhost:5829`** to access Lucy’s interactive interface. (Port 5829 spells “LUCY” on a phone keypad.) You will be greeted with a local web app where you can chat with Lucy and access dashboards.

After installation, Lucy will perform an initial hardware scan and automatically select the optimal AI model configuration for your device (e.g., using a smaller quantized model if you have lower RAM, or enabling more advanced reasoning models if you have a powerful GPU). The first startup may involve a brief setup as models are loaded and optimized.

**Local Optimization (Optional):** Advanced users can enable Lucy’s autonomous optimization agents to run in the background. These agents will continuously tune performance and personalize the system. For example, you can run:

```sh
lucy --enable-optimization
```

to allow Lucy’s local performance agents to start, and you can configure preferences (like how aggressive it should be in adapting to hardware or cleaning up resources) using the config file. Lucy’s default settings already provide a balanced performance, so this step is optional.

**Using Lucy:** Interact with Lucy through the chat interface in your browser. You can ask questions, talk about your day, work through a CBT exercise, or seek peak-performance coaching. Lucy will respond with empathy and evidence-based suggestions. All data stays local, and you can explore various dashboards for **Privacy** (to review what data is stored), **Performance** (to see how the system is optimizing), and **Health** (to check all agents are running smoothly) at the following local URLs:

* `http://localhost:5830/local` – Local Performance Monitor dashboard
* `http://localhost:5831/privacy` – Privacy & Data governance dashboard
* `http://localhost:5832/health` – System health status dashboard

*(The above are accessible only on your machine and are optional tools for power users; the primary interaction is via the chat interface.)*

For any issues during setup or runtime, consult the **Community and Support** section of the README or open an issue on GitHub. Lucy is under active development, and we welcome feedback to improve the installation and user experience.

### Legal & Disclaimers

- Lucy in the Loop is open-source AI software and is not a doctor, therapist, or emergency service. Use at your own risk.
- Do not use in high-risk settings (e.g., clinical decision-making or life support).
- Privacy is local-first/offline by design.
- See: [`DISCLAIMER.md`](./DISCLAIMER.md), [`TERMS.md`](./TERMS.md), [`MEDICAL-DISCLAIMER.md`](./MEDICAL-DISCLAIMER.md), and [`docs/privacy-policy.md`](./docs/privacy-policy.md).
- Related policies: [`docs/safety-risk-disclosure.md`](./docs/safety-risk-disclosure.md), [`docs/transparent-autonomy-policy.md`](./docs/transparent-autonomy-policy.md), [`docs/failsafe-and-kill-switch-protocols.md`](./docs/failsafe-and-kill-switch-protocols.md), [`docs/ethics-compliance-manifesto.md`](./docs/ethics-compliance-manifesto.md).
