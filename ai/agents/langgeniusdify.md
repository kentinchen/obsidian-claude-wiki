---
title: "langgenius/dify: Production-ready platform for agentic workflow development."
source: "https://github.com/langgenius/dify"
author:
published:
created: 2026-04-16
description: "Production-ready platform for agentic workflow development. - langgenius/dify"
tags:
  - "clippings"
---
[![cover-v5-optimized](https://github.com/langgenius/dify/raw/main/images/GitHub_README_if.png)](https://github.com/langgenius/dify/blob/main/images/GitHub_README_if.png)

[Dify Cloud](https://cloud.dify.ai/) · [Self-hosting](https://docs.dify.ai/getting-started/install-self-hosted) · [Documentation](https://docs.dify.ai/) · [Dify edition overview](https://dify.ai/pricing)

[![follow on X(Twitter)](https://camo.githubusercontent.com/b0e144d3c181c9dca1078e6a6f9e2c5f6fb82ef2e9f4e359d922185981bf2b5d/68747470733a2f2f696d672e736869656c64732e696f2f747769747465722f666f6c6c6f772f646966795f61693f6c6f676f3d5826636f6c6f723d253230253233663566356635)](https://twitter.com/intent/follow?screen_name=dify_ai) [![follow on LinkedIn](https://camo.githubusercontent.com/1a852179777588c4aec0e6def69584359cf40afcc622e556f91c52c620706c6c/68747470733a2f2f637573746f6d2d69636f6e2d6261646765732e64656d6f6c61622e636f6d2f62616467652f4c696e6b6564496e2d3041363643323f6c6f676f3d6c696e6b6564696e2d7768697465266c6f676f436f6c6f723d666666)](https://www.linkedin.com/company/langgenius/) [![Docker Pulls](https://camo.githubusercontent.com/401d6759eab0b34cecc8bbdc431c354d71fcfdd62a302179c28868480d430b0c/68747470733a2f2f696d672e736869656c64732e696f2f646f636b65722f70756c6c732f6c616e6767656e6975732f646966792d7765623f6c6162656c436f6c6f723d25323025323346444230363226636f6c6f723d253230253233663739303039)](https://hub.docker.com/u/langgenius) [![Commits last month](https://camo.githubusercontent.com/2b0fc07bd2325240873db8c71bc596c1e4739971aa199b36645974d5b7543e4b/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f636f6d6d69742d61637469766974792f6d2f6c616e6767656e6975732f646966793f6c6162656c436f6c6f723d25323025323333326235383326636f6c6f723d253230253233313262373661)](https://github.com/langgenius/dify/graphs/commit-activity) [![Issues closed](https://camo.githubusercontent.com/6c8501833b2ed241cbacca24bb6494e79e990cbd96065e35103bf583f1580fc6/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6973737565732d7365617263683f71756572793d7265706f2533416c616e6767656e697573253246646966792532306973253341636c6f736564266c6162656c3d697373756573253230636c6f736564266c6162656c436f6c6f723d25323025323337643839623026636f6c6f723d253230253233356436623938)](https://github.com/langgenius/dify/) [![Discussion posts](https://camo.githubusercontent.com/0fb711b5455df6c54d5b85fd394af06f80bebdf63193126656ec6f52ceff91c2/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f64697363757373696f6e732f6c616e6767656e6975732f646966793f6c6162656c436f6c6f723d25323025323339623861666226636f6c6f723d253230253233376135616638)](https://github.com/langgenius/dify/discussions/)

Dify is an open-source LLM app development platform. Its intuitive interface combines AI workflow, RAG pipeline, agent capabilities, model management, observability features (including [Opik](https://www.comet.com/docs/opik/integrations/dify), [Langfuse](https://docs.langfuse.com/), and [Arize Phoenix](https://docs.arize.com/phoenix)) and more, letting you quickly go from prototype to production. Here's a list of the core features:

## Quick start

> Before installing Dify, make sure your machine meets the following minimum system requirements:
> 
> - CPU >= 2 Core
> - RAM >= 4 GiB

  

The easiest way to start the Dify server is through [Docker Compose](https://github.com/langgenius/dify/blob/main/docker/docker-compose.yaml). Before running Dify with the following commands, make sure that [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/) are installed on your machine:

```
cd dify
cd docker
cp .env.example .env
docker compose up -d
```

After running, you can access the Dify dashboard in your browser at [http://localhost/install](http://localhost/install) and start the initialization process.

#### Seeking help

Please refer to our [FAQ](https://docs.dify.ai/getting-started/install-self-hosted/faqs) if you encounter problems setting up Dify. Reach out to [the community and us](#community--contact) if you are still having issues.

> If you'd like to contribute to Dify or do additional development, refer to our [guide to deploying from source code](https://docs.dify.ai/getting-started/install-self-hosted/local-source-code)

## Key features

**1\. Workflow**: Build and test powerful AI workflows on a visual canvas, leveraging all the following features and beyond.

**2\. Comprehensive model support**: Seamless integration with hundreds of proprietary / open-source LLMs from dozens of inference providers and self-hosted solutions, covering GPT, Mistral, Llama3, and any OpenAI API-compatible models. A full list of supported model providers can be found [here](https://docs.dify.ai/getting-started/readme/model-providers).

[![providers-v5](https://private-user-images.githubusercontent.com/13230914/321881730-5a17bdbe-097a-4100-8363-40255b70f6e3.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDg3NTIsIm5iZiI6MTc3NjM0ODQ1MiwicGF0aCI6Ii8xMzIzMDkxNC8zMjE4ODE3MzAtNWExN2JkYmUtMDk3YS00MTAwLTgzNjMtNDAyNTViNzBmNmUzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE0MDczMlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTdmOWMzMTAxNGQxYWJhODE4N2QwNzM1Yjg4NTUyNGI4N2I1ZDUxN2QwNTg1ZDhkZjY4NjFlMDI1ZDUwNDU3MzgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.37XZUSojnyHvUAzIUlMbQTmINOCf85BsOXD5NhfoQns)](https://private-user-images.githubusercontent.com/13230914/321881730-5a17bdbe-097a-4100-8363-40255b70f6e3.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDg3NTIsIm5iZiI6MTc3NjM0ODQ1MiwicGF0aCI6Ii8xMzIzMDkxNC8zMjE4ODE3MzAtNWExN2JkYmUtMDk3YS00MTAwLTgzNjMtNDAyNTViNzBmNmUzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE0MDczMlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTdmOWMzMTAxNGQxYWJhODE4N2QwNzM1Yjg4NTUyNGI4N2I1ZDUxN2QwNTg1ZDhkZjY4NjFlMDI1ZDUwNDU3MzgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.37XZUSojnyHvUAzIUlMbQTmINOCf85BsOXD5NhfoQns)

**3\. Prompt IDE**: Intuitive interface for crafting prompts, comparing model performance, and adding additional features such as text-to-speech to a chat-based app.

**4\. RAG Pipeline**: Extensive RAG capabilities that cover everything from document ingestion to retrieval, with out-of-box support for text extraction from PDFs, PPTs, and other common document formats.

**5\. Agent capabilities**: You can define agents based on LLM Function Calling or ReAct, and add pre-built or custom tools for the agent. Dify provides 50+ built-in tools for AI agents, such as Google Search, DALL·E, Stable Diffusion and WolframAlpha.

**6\. LLMOps**: Monitor and analyze application logs and performance over time. You could continuously improve prompts, datasets, and models based on production data and annotations.

**7\. Backend-as-a-Service**: All of Dify's offerings come with corresponding APIs, so you could effortlessly integrate Dify into your own business logic.

## Using Dify

- **Cloud  
	**We host a [Dify Cloud](https://dify.ai/) service for anyone to try with zero setup. It provides all the capabilities of the self-deployed version, and includes 200 free GPT-4 calls in the sandbox plan.
- **Self-hosting Dify Community Edition  
	**Quickly get Dify running in your environment with this [starter guide](#quick-start). Use our [documentation](https://docs.dify.ai/) for further references and more in-depth instructions.
- **Dify for enterprise / organizations  
	**We provide additional enterprise-centric features. [Send us an email](mailto:business@dify.ai?subject=%5BGitHub%5DBusiness%20License%20Inquiry) to discuss your enterprise needs.  
	> For startups and small businesses using AWS, check out [Dify Premium on AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-t22mebxzwjhu6) and deploy it to your own AWS VPC with one click. It's an affordable AMI offering with the option to create apps with custom logo and branding.

## Staying ahead

Star Dify on GitHub and be instantly notified of new releases.

[![star-us](https://private-user-images.githubusercontent.com/13230914/320902970-b823edc1-6388-4e25-ad45-2f6b187adbb4.gif?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDg3NTIsIm5iZiI6MTc3NjM0ODQ1MiwicGF0aCI6Ii8xMzIzMDkxNC8zMjA5MDI5NzAtYjgyM2VkYzEtNjM4OC00ZTI1LWFkNDUtMmY2YjE4N2FkYmI0LmdpZj9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE0MDczMlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTQzNWRjNDM5OGRhZDMzN2YxOGZlMDhjOTA2ZDEzMzhhZTQ4YmJkZjYyNDM2ODBlZWU1NGNhNzk3ODM0ZWJhMWMmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRmdpZiJ9.FxXR9gCW89N7hkUK3R-0MYLnjr3R_Nch06UeE5CpHYY)](https://private-user-images.githubusercontent.com/13230914/320902970-b823edc1-6388-4e25-ad45-2f6b187adbb4.gif?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNDg3NTIsIm5iZiI6MTc3NjM0ODQ1MiwicGF0aCI6Ii8xMzIzMDkxNC8zMjA5MDI5NzAtYjgyM2VkYzEtNjM4OC00ZTI1LWFkNDUtMmY2YjE4N2FkYmI0LmdpZj9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA0MTYlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwNDE2VDE0MDczMlomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTQzNWRjNDM5OGRhZDMzN2YxOGZlMDhjOTA2ZDEzMzhhZTQ4YmJkZjYyNDM2ODBlZWU1NGNhNzk3ODM0ZWJhMWMmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRmdpZiJ9.FxXR9gCW89N7hkUK3R-0MYLnjr3R_Nch06UeE5CpHYY)

## Advanced Setup

### Custom configurations

If you need to customize the configuration, please refer to the comments in our [.env.example](https://github.com/langgenius/dify/blob/main/docker/.env.example) file and update the corresponding values in your `.env` file. Additionally, you might need to make adjustments to the `docker-compose.yaml` file itself, such as changing image versions, port mappings, or volume mounts, based on your specific deployment environment and requirements. After making any changes, please re-run `docker compose up -d`. You can find the full list of available environment variables [here](https://docs.dify.ai/getting-started/install-self-hosted/environments).

#### Customizing Suggested Questions

You can now customize the "Suggested Questions After Answer" feature to better fit your use case. For example, to generate longer, more technical questions:

```
# In your .env file
SUGGESTED_QUESTIONS_PROMPT='Please help me predict the five most likely technical follow-up questions a developer would ask. Focus on implementation details, best practices, and architecture considerations. Keep each question between 40-60 characters. Output must be JSON array: ["question1","question2","question3","question4","question5"]'
SUGGESTED_QUESTIONS_MAX_TOKENS=512
SUGGESTED_QUESTIONS_TEMPERATURE=0.3
```

See the [Suggested Questions Configuration Guide](https://github.com/langgenius/dify/blob/main/docs/suggested-questions-configuration.md) for detailed examples and usage instructions.

### Metrics Monitoring with Grafana

Import the dashboard to Grafana, using Dify's PostgreSQL database as data source, to monitor metrics in granularity of apps, tenants, messages, and more.

- [Grafana Dashboard by @bowenliang123](https://github.com/bowenliang123/dify-grafana-dashboard)

### Deployment with Kubernetes

If you'd like to configure a highly-available setup, there are community-contributed [Helm Charts](https://helm.sh/) and YAML files which allow Dify to be deployed on Kubernetes.

- [Helm Chart by @LeoQuote](https://github.com/douban/charts/tree/master/charts/dify)
- [Helm Chart by @BorisPolonsky](https://github.com/BorisPolonsky/dify-helm)
- [Helm Chart by @magicsong](https://github.com/magicsong/ai-charts)
- [YAML file by @Winson-030](https://github.com/Winson-030/dify-kubernetes)
- [YAML file by @wyy-holding](https://github.com/wyy-holding/dify-k8s)
- [🚀 NEW! YAML files (Supports Dify v1.6.0) by @Zhoneym](https://github.com/Zhoneym/DifyAI-Kubernetes)

#### Using Terraform for Deployment

Deploy Dify to Cloud Platform with a single click using [terraform](https://www.terraform.io/)

##### Azure Global

- [Azure Terraform by @nikawang](https://github.com/nikawang/dify-azure-terraform)

##### Google Cloud

- [Google Cloud Terraform by @sotazum](https://github.com/DeNA/dify-google-cloud-terraform)

#### Using AWS CDK for Deployment

Deploy Dify to AWS with [CDK](https://aws.amazon.com/cdk/)

##### AWS

- [AWS CDK by @KevinZhao (EKS based)](https://github.com/aws-samples/solution-for-deploying-dify-on-aws)
- [AWS CDK by @tmokmss (ECS based)](https://github.com/aws-samples/dify-self-hosted-on-aws)

#### Using Alibaba Cloud Computing Nest

Quickly deploy Dify to Alibaba cloud with [Alibaba Cloud Computing Nest](https://computenest.console.aliyun.com/service/instance/create/default?type=user&ServiceName=Dify%E7%A4%BE%E5%8C%BA%E7%89%88)

#### Using Alibaba Cloud Data Management

One-Click deploy Dify to Alibaba Cloud with [Alibaba Cloud Data Management](https://www.alibabacloud.com/help/en/dms/dify-in-invitational-preview/)

#### Deploy to AKS with Azure Devops Pipeline

One-Click deploy Dify to AKS with [Azure Devops Pipeline Helm Chart by @LeoZhang](https://github.com/Ruiruiz30/Dify-helm-chart-AKS)

## Contributing

For those who'd like to contribute code, see our [Contribution Guide](https://github.com/langgenius/dify/blob/main/CONTRIBUTING.md). At the same time, please consider supporting Dify by sharing it on social media and at events and conferences.

> We are looking for contributors to help translate Dify into languages other than Mandarin or English. If you are interested in helping, please see the [i18n README](https://github.com/langgenius/dify/blob/main/web/i18n-config/README.md) for more information, and leave us a comment in the `global-users` channel of our [Discord Community Server](https://discord.gg/8Tpq4AcN9c).

## Community & contact

- [GitHub Discussion](https://github.com/langgenius/dify/discussions). Best for: sharing feedback and asking questions.
- [GitHub Issues](https://github.com/langgenius/dify/issues). Best for: bugs you encounter using Dify.AI, and feature proposals. See our [Contribution Guide](https://github.com/langgenius/dify/blob/main/CONTRIBUTING.md).
- [Discord](https://discord.gg/FngNHpbcY7). Best for: sharing your applications and hanging out with the community.
- [X(Twitter)](https://twitter.com/dify_ai). Best for: sharing your applications and hanging out with the community.

**Contributors**

[![](https://camo.githubusercontent.com/f05767d54be81bc8629056a2685e98f03374773215f1ddf6e4e17439107cd4c9/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d6c616e6767656e6975732f64696679)](https://github.com/langgenius/dify/graphs/contributors)

## Star history

[![Star History Chart](https://camo.githubusercontent.com/66c47963aa4beb93353ebe7d3c33a84ab8d0114a39a31207f9135c5029578bb1/68747470733a2f2f6170692e737461722d686973746f72792e636f6d2f7376673f7265706f733d6c616e6767656e6975732f6469667926747970653d44617465)](https://star-history.com/#langgenius/dify&Date)

## Security disclosure

To protect your privacy, please avoid posting security issues on GitHub. Instead, report issues to [security@dify.ai](mailto:security@dify.ai), and our team will respond with detailed answer.

## License

This repository is licensed under the [Dify Open Source License](https://github.com/langgenius/dify/blob/main/LICENSE), based on Apache 2.0 with additional conditions.