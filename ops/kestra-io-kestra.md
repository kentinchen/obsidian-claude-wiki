---
title: "kestra-io/kestra: Event Driven Orchestration & Scheduling Platform for Mission Critical Applications"
source: "https://github.com/kestra-io/kestra"
author:
published:
created: 2026-04-17
description: "Event Driven Orchestration & Scheduling Platform for Mission Critical Applications - kestra-io/kestra"
tags:
  - "clippings"
---
[![Kestra workflow orchestrator](https://camo.githubusercontent.com/1294b56f28712082490368b696cf31b02c6b0876f8530b904eb47778fd79b82b/68747470733a2f2f6b65737472612e696f2f62616e6e65722e706e67)](https://www.kestra.io/)

## Event-Driven Declarative Orchestration Platform

[![Last Version](https://camo.githubusercontent.com/9e0246ad8abb4c682abf3fd1a141b249f0ec263a18505c2b8208cbc7a3b58faf/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f7461672d7072652f6b65737472612d696f2f6b65737472612e7376673f636f6c6f723d626c756576696f6c6574)](https://github.com/kestra-io/kestra/releases)  
[![Slack](https://camo.githubusercontent.com/8e5f533ca0cb3da8db16c72891392b23124c250c0c6901e5a8d12c43aa35a475/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f536c61636b2d4a6f696e253230436f6d6d756e6974792d626c756576696f6c65743f6c6f676f3d736c61636b)](https://kestra.io/slack)

  

 [![kestra-io%2Fkestra | Trendshift](https://camo.githubusercontent.com/ffd036ced721268e62fb7faa6900010c09575f12428fb0c58e0bdaec5df1032d/68747470733a2f2f7472656e6473686966742e696f2f6170692f62616467652f7265706f7369746f726965732f32373134)](https://trendshift.io/repositories/2714)[![Kestra - All-in-one automation & orchestration platform | Product Hunt](https://camo.githubusercontent.com/e71680187e35a9996a29bd532096101fe82b3c7fd6a12a70d8f93f59da733985/68747470733a2f2f6170692e70726f6475637468756e742e636f6d2f776964676574732f656d6265642d696d6167652f76312f746f702d706f73742d62616467652e7376673f706f73745f69643d363132303737267468656d653d6c6967687426706572696f643d6461696c7926743d31373430373337353036313632)](https://www.producthunt.com/posts/kestra?embed=true&utm_source=badge-top-post-badge&utm_medium=badge&utm_souce=badge-kestra)

[![Get started in 3 minutes with Kestra](https://camo.githubusercontent.com/20bbaf8f5cc48674b3bc3bf7cf7718998b203ea06c29b3b57d22489a314fa922/68747470733a2f2f6b65737472612e696f2f7374617274766964656f2e706e67)](https://go.kestra.io/video/product-overview)

*Click on the image to learn how to get started with Kestra in 3 minutes.*

## 🌟 What is Kestra?

Kestra is an open-source, event-driven orchestration platform that makes both **scheduled** and **event-driven** workflows easy. By bringing **Infrastructure as Code** best practices to data, process, and microservice orchestration, you can build reliable [workflows](https://kestra.io/docs/getting-started) directly from the UI in just a few lines of YAML.

**Key Features:**

- **Everything as Code and from the UI:** keep **workflows as code** with a **Git Version Control** integration, even when building them from the UI.
- **Event-Driven & Scheduled Workflows:** automate both **scheduled** and **real-time** event-driven workflows via a simple `trigger` definition.
- **Declarative YAML Interface:** define workflows using a simple configuration in the **built-in code editor**.
- **Rich Plugin Ecosystem:** hundreds of plugins built in to extract data from any database, cloud storage, or API, and **run scripts in any language**.
- **Intuitive UI & Code Editor:** build and visualize workflows directly from the UI with syntax highlighting, auto-completion and real-time syntax validation.
- **Scalable:** designed to handle millions of workflows, with high availability and fault tolerance.
- **Version Control Friendly:** write your workflows from the built-in code Editor and push them to your preferred Git branch directly from Kestra, enabling best practices with CI/CD pipelines and version control systems.
- **Structure & Resilience**: tame chaos and bring resilience to your workflows with **namespaces**, **labels**, **subflows**, **retries**, **timeout**, **error handling**, **inputs**, **outputs** that generate artifacts in the UI, **variables**, **conditional branching**, **advanced scheduling**, **event triggers**, **backfills**, **dynamic tasks**, **sequential and parallel tasks**, and skip tasks or triggers when needed by setting the flag `disabled` to `true`.

🧑💻 The YAML definition gets automatically adjusted any time you make changes to a workflow from the UI or via an API call. Therefore, the orchestration logic is **always managed declaratively in code**, even if you modify your workflows in other ways (UI, CI/CD, Terraform, API calls).

[![Adding new tasks in the UI](https://camo.githubusercontent.com/f7d99b70a716e644f98be8e585342e1b2c79aa68ba10dd9fb5721887724dffff/68747470733a2f2f6b65737472612e696f2f616464696e672d7461736b732e676966)](https://camo.githubusercontent.com/f7d99b70a716e644f98be8e585342e1b2c79aa68ba10dd9fb5721887724dffff/68747470733a2f2f6b65737472612e696f2f616464696e672d7461736b732e676966)

---

## 🚀 Quick Start

### Launch on AWS (CloudFormation)

Deploy Kestra on AWS using our CloudFormation template:

### Launch on Google Cloud (Terraform deployment)

Deploy Kestra on Google Cloud Infrastructure Manager using [our Terraform module](https://github.com/kestra-io/deployment-templates/tree/main/gcp/terraform/infrastructure-manager/vm-sql-gcs).

### Get Started Locally in 5 Minutes

#### Launch Kestra in Docker

Make sure that Docker is running. Then, start Kestra in a single command:

```
docker run --pull=always -it -p 8080:8080 --user=root \
  --name kestra --restart=always \
  -v kestra_data:/app/storage \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /tmp:/tmp \
  kestra/kestra:latest server local
```

If you're on Windows and use PowerShell:

```
docker run --pull=always -it -p 8080:8080 --user=root \`
  --name kestra --restart=always \`
  -v "kestra_data:/app/storage" \`
  -v "/var/run/docker.sock:/var/run/docker.sock" \`
  -v "C:/Temp:/tmp" \`
  kestra/kestra:latest server local
```

If you're on Windows and use Command Prompt (CMD):

```
docker run --pull=always -it -p 8080:8080 --user=root ^
  --name kestra --restart=always ^
  -v "kestra_data:/app/storage" ^
  -v "/var/run/docker.sock:/var/run/docker.sock" ^
  -v "C:/Temp:/tmp" ^
  kestra/kestra:latest server local
```

If you're on Windows and use WSL (Linux-based environment in Windows):

```
docker run --pull=always -it -p 8080:8080 --user=root \
  --name kestra --restart=always \
  -v kestra_data:/app/storage \
  -v "/var/run/docker.sock:/var/run/docker.sock" \
  -v "/mnt/c/Temp:/tmp" \
  kestra/kestra:latest server local
```

Check our [Installation Guide](https://kestra.io/docs/installation) for other deployment options (Docker Compose, Podman, Kubernetes, AWS, GCP, Azure, and more).

Access the Kestra UI at [http://localhost:8080](http://localhost:8080/) and start building your first flow!

#### Your First Hello World Flow

Create a new flow with the following content:

```
id: hello_world
namespace: dev

tasks:
  - id: say_hello
    type: io.kestra.plugin.core.log.Log
    message: "Hello, World!"
```

Run the flow and see the output in the UI!

---

## 🧩 Plugin Ecosystem

Kestra's functionality is extended through a rich [ecosystem of plugins](https://kestra.io/plugins) that empower you to run tasks anywhere and code in any language, including Python, Node.js, R, Go, Shell, and more. Here's how Kestra plugins enhance your workflows:

- **Run Anywhere:**
	- **Local or Remote Execution:** Execute tasks on your local machine, remote servers via SSH, or scale out to serverless containers using [Task Runners](https://kestra.io/docs/task-runners).
		- **Docker and Kubernetes Support:** Seamlessly run Docker containers within your workflows or launch Kubernetes jobs to handle compute-intensive workloads.
- **Code in Any Language:**
	- **Scripting Support:** Write scripts in your preferred programming language. Kestra supports Python, Node.js, R, Go, Shell, and others, allowing you to integrate existing codebases and deployment patterns.
		- **Flexible Automation:** Execute shell commands, run SQL queries against various databases, and make HTTP requests to interact with APIs.
- **Event-Driven and Real-Time Processing:**
	- **Real-Time Triggers:** React to events from external systems in real-time, such as file arrivals, new messages in message buses (Kafka, Redis, Pulsar, AMQP, MQTT, NATS, AWS SQS, Google Pub/Sub, Azure Event Hubs), and more.
		- **Custom Events:** Define custom events to trigger flows based on specific conditions or external signals, enabling highly responsive workflows.
- **Cloud Integrations:**
	- **AWS, Google Cloud, Azure:** Integrate with a variety of cloud services to interact with storage solutions, messaging systems, compute resources, and more.
		- **Big Data Processing:** Run big data processing tasks using tools like Apache Spark or interact with analytics platforms like Google BigQuery.
- **Monitoring and Notifications:**
	- **Stay Informed:** Send messages to Slack channels, email notifications, or trigger alerts in PagerDuty to keep your team updated on workflow statuses.

Kestra's plugin ecosystem is continually expanding, allowing you to tailor the platform to your specific needs. Whether you're orchestrating complex data pipelines, automating scripts across multiple environments, or integrating with cloud services, there's likely a plugin to assist. And if not, you can always [build your own plugins](https://kestra.io/docs/plugin-developer-guide/) to extend Kestra's capabilities.

🧑💻 **Note:** This is just a glimpse of what Kestra plugins can do. Explore the full list on our [Plugins Page](https://kestra.io/plugins).

---

## 📚 Key Concepts

- **Flows:** the core unit in Kestra, representing a workflow composed of tasks.
- **Tasks:** individual units of work, such as running a script, moving data, or calling an API.
- **Namespaces:** logical grouping of flows for organization and isolation.
- **Triggers:** schedule or events that initiate the execution of flows.
- **Inputs & Variables:** parameters and dynamic data passed into flows and tasks.

---

## 🎨 Build Workflows Visually

Kestra provides an intuitive UI that allows you to interactively build and visualize your workflows:

- **Drag-and-Drop Interface:** add and rearrange tasks from the Topology Editor.
- **Real-Time Validation:** instant feedback on your workflow's syntax and structure to catch errors early.
- **Auto-Completion:** smart suggestions as you type to write flow code quickly and without syntax errors.
- **Live Topology View:** see your workflow as a Directed Acyclic Graph (DAG) that updates in real-time.

---

## 🔧 Extensible and Developer-Friendly

### Plugin Development

Create custom plugins to extend Kestra's capabilities. Check out our [Plugin Developer Guide](https://kestra.io/docs/plugin-developer-guide/) to get started.

### Infrastructure as Code

- **Version Control:** store your flows in Git repositories.
- **CI/CD Integration:** automate deployment of flows using CI/CD pipelines.
- **Terraform Provider:** manage Kestra resources with the [official Terraform provider](https://kestra.io/docs/terraform/).

---

## 🌐 Join the Community

Stay connected and get support:

- **Slack:** Join our [Slack community](https://kestra.io/slack) to ask questions and share ideas.
- **LinkedIn:** Follow us on [LinkedIn](https://www.linkedin.com/company/kestra/) — next to Slack and GitHub, this is our main channel to share updates and product announcements.
- **YouTube:** Subscribe to our [YouTube channel](https://www.youtube.com/@kestra-io) for educational video content. We publish new videos every week!
- **X:** Follow us on [X](https://x.com/kestra_io) if you're still active there.

---

## 🤝 Contributing

We welcome contributions of all kinds!

- **Report Issues:** Found a bug or have a feature request? Open an [issue on GitHub](https://github.com/kestra-io/kestra/issues).
- **Contribute Code:** Check out our [Contributor Guide](https://kestra.io/docs/contribute-to-kestra) for initial guidelines, and explore our [good first issues](https://go.kestra.io/contributing) for beginner-friendly tasks to tackle first.
- **Develop Plugins:** Build and share plugins using our [Plugin Developer Guide](https://kestra.io/docs/plugin-developer-guide/).
- **Contribute to our Docs:** Contribute edits or updates to keep our [documentation](https://github.com/kestra-io/docs) top-notch.

---

## 📄 License

Kestra is licensed under the Apache 2.0 License © [Kestra Technologies](https://kestra.io/).

---

## ⭐️ Stay Updated

Give our repository a star to stay informed about the latest features and updates!

[![Star the Repo](https://camo.githubusercontent.com/6e62da867f7047c2047a814161b3d0e18155b5b44d4678af722ddf8b9e926147/68747470733a2f2f6b65737472612e696f2f737461722e676966)](https://github.com/kestra-io/kestra)

---

Thank you for considering Kestra for your workflow orchestration needs. We can't wait to see what you'll build!