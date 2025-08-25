## Privacy Policy

**Last Updated:** August 2025

Note: This policy describes intended behavior of the application. As of now, the repository contains documentation and policies only; application features referenced here will be implemented in forthcoming releases.

Your privacy is of paramount importance in Lucy in the Loop. This Privacy Policy explains what data Lucy handles, how it is protected, and the measures in place to ensure your personal information remains confidential. Our guiding principle is simple: *your data stays with you*. Lucy is designed as a fully offline system specifically to safeguard your privacy.

### Data Collection & Storage

* **No Cloud Storage (Default):** Lucy **does not send or store any personal data on external servers or the cloud by default**. All data (conversation history, user profiles, settings, etc.) is stored locally on the user’s own device. This local-first approach reduces exposure of sensitive information to third parties.
* **Types of Data:** The data Lucy may handle includes the text of your conversations with the AI, any goals or notes you input, and configuration settings. Lucy does **not** require any personally identifying information to function; you may use it anonymously or with a nickname. It does not automatically collect metadata like your location or contacts. The only usage data collected are internal metrics (e.g., number of sessions, performance stats) which remain on-device and are used solely to optimize your experience.
* **Data Minimization:** Lucy actively minimizes the data it keeps. It only retains information that is essential for providing the service and improving the AI’s responses to you. For example, it might store summary embeddings of past conversations to maintain context, rather than raw transcripts, whenever possible. Unnecessary data is either not recorded at all or promptly deleted.

### Data Use and Processing

* **Personalization:** Any personal data (such as mood logs you enter or feedback you give) is used **only to personalize your experience** and provide more relevant support. Lucy’s **Personalization Agent** learns from your interactions to tailor strategies that work best for you, but this learning happens locally on your device and is not shared.
* **No Profiling for Marketing:** Lucy does not profile you for advertising or sell your data. There are no ads in Lucy. You will never find your conversations being used to target you with products or shared with analytics companies.
* **AI Model Behavior:** The AI models running within Lucy may analyze your text inputs to generate helpful responses (that’s how the AI works), but they do so on the fly, in memory. The models do not produce lasting records of your inputs except what is needed for context in ongoing conversations, which is kept locally.

### Data Protection & Security

* **Encryption:** All sensitive data that Lucy stores locally (such as conversation histories or any personal journal entries you save) is encrypted at rest on your device. Lucy’s **Privacy Agent** includes an *Encryption Manager* that handles key management and ensures your data is stored using strong encryption (AES-256 or equivalent). This means that even if someone gains access to your device’s files, the data related to Lucy would be unreadable without proper authorization.
* **Access Controls:** Lucy enforces strict access controls consistent with a “zero-trust” approach. Only the core Lucy application and its sandboxed agents can access your data, and even among agents, access is compartmentalized to only what each needs. For example, the Therapeutic Agent may access conversation content, but a Maintenance Agent optimizing code has no access to your conversation logs. There is continuous authentication and authorization checking for any agent action that touches user data.
* **Local Only Mode:** By default, Lucy runs in *offline-only mode*. It does not require internet connectivity, and unless you explicitly opt-in to some connectivity (e.g., checking for software updates or participating in federated learning – features not enabled by default), it will not transmit any data out. In your settings (`~/.lucy/local-config.yaml`), the `offline_only` flag is enabled to guarantee this.
* **Data Retention and Deletion:** Lucy implements an automatic data deletion schedule. By default, personal conversation data older than a certain number of days (e.g., 90 days) is securely wiped from the local storage, unless you choose to retain it longer. This retention period is configurable. The **Deletion Scheduler** agent performs periodic cleanup, ensuring that data isn’t kept longer than necessary. You can also manually delete all your data at any time – either through the privacy dashboard or by a command – and Lucy will erase all stored user content, confirming with you first. We design these features so you can always exercise *your “right to be forgotten”*.
* **Consent Management:** On first use, Lucy will present you with this privacy policy and ask for your consent to proceed. Throughout use, if any feature would involve using your data in a new way, Lucy will transparently ask for permission via the **Consent Manager** (for example, if in the future you opt-in to share anonymized data to improve the global model, that will be a clear opt-in choice). If you decline, Lucy will respect that and disable that feature. We log your consent decisions locally with timestamps for auditability.
* **No Third-Party Access:** Quantum Pipes (the maintainers) and community contributors do *not* have access to individual user data. We do not collect analytics from your device. All development and improvement of Lucy happens either on volunteer-provided test data or via synthetic data. You are effectively running a standalone app – we don’t see or touch your data.

### Compliance and Transparency

* **HIPAA, HBNR, and State Health‑Privacy Laws:** Lucy is designed to minimize regulated data exposure. Stand‑alone wellness apps are typically not subject to HIPAA unless operated by a covered entity or business associate. However, the FTC **Health Breach Notification Rule (HBNR)** and certain state health‑privacy laws (e.g., Washington My Health My Data Act, California CPRA/CMIA) may apply if there is a breach or certain processing of consumer health data. We maintain an incident playbook (see SECURITY.md) and will follow applicable notification requirements.
* **GDPR and EU/UK Privacy:** For EU/UK users, Lucy’s on‑device model means you control your data. If optional connectivity features are enabled, we will provide appropriate disclosures, lawful bases, and data subject rights mechanisms where applicable.
* **Transparency:** We disclose all aspects of data handling in our open-source code. Users and developers can inspect the codebase to verify that we are not secretly transmitting data. Our **Compliance Validator** agent automatically audits the system against privacy requirements and logs a compliance report that you can view. If any component of Lucy ever tries to do something disallowed (like an agent requesting internet access when in offline mode), it will be blocked and reported.
* **User Rights:** Because all data is on your device, you inherently have full control. You have the right to export your data (in planned builds, this will be available via an export function; until then, data would be stored locally in accessible formats). You also have the right to delete your data completely, as mentioned. There are no external “accounts” with Lucy, so data access requests or corrections are all in your hands locally.

### Changes to Privacy Policy

Any changes to this Privacy Policy (for example, if we add an optional cloud feature or integrate an update mechanism) will be communicated in advance. Lucy will notify you of changes and seek your consent if the changes materially affect how your data is handled. We also version-control this policy in the repository so the community can see the exact history of modifications.

If you have any questions or concerns about privacy while using Lucy in the Loop, please reach out via the project’s GitHub issues or discussion forum. Privacy isn’t just a legal formality for us – it’s a core value built into Lucy’s very architecture.

*(By using Lucy in the Loop, you acknowledge that you have read and agree to this Privacy Policy.)*
