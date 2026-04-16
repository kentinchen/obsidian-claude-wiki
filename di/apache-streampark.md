---
title: "apache/streampark: Make stream processing easier! Easy-to-use streaming application development framework and operation platform."
source: "https://github.com/apache/streampark"
author:
published:
created: 2026-04-17
description: "Make stream processing easier! Easy-to-use streaming application development framework and operation platform. - apache/streampark"
tags:
  - "clippings"
---
## Apache StreamPark

[![StreamPark logo](https://camo.githubusercontent.com/b60f78c7d97557a47076feed4ecd60f641995546015df8b7f5ac48926c0ce114/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f6c6f676f5f6e616d652e706e67)](https://camo.githubusercontent.com/b60f78c7d97557a47076feed4ecd60f641995546015df8b7f5ac48926c0ce114/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f6c6f676f5f6e616d652e706e67)

**StreamPark**: a streaming application development framework and cloud-native real-time computing platform.

## 📊 Overview

**StreamPark** is an open-source framework for building and managing real-time streaming applications, designed to simplify the end-to-end lifecycle of stream processing. It provides a unified development framework for Apache Flink and Apache Spark, along with a powerful cloud-native platform for application management.

StreamPark enables users to develop, debug, deploy, and operate large-scale streaming applications efficiently and consistently. Originally named StreamX, the project was renamed StreamPark in August 2022 and became an Apache Top-Level Project (TLP) in January 2025.

- **Streaming Application Development Framework**
	- Simplifies Flink and Spark streaming development with prebuilt APIs, connectors, and templates.
- **Cloud-Native Real-Time Computing Platform**
	- Offers a one-stop real-time computing platform for development, deployment, monitoring, and operations.
- **Unified Batch & Streaming Processing**
	- Supports Apache Flink and Apache Spark, enabling both stream processing and batch processing.
- **Multi-Engine & Multi-Version Support**
	- Run and manage multi-version Flink/Spark applications.
- **Multi-Environment Compatibility**
	- Works on Standalone, YARN (Hadoop 2.x/3.x), and Kubernetes.
- **Rich Ecosystems**
	- Compatible with big-data ecosystem tools (e.g., Apache Flink/Spark/Paimon/Doris) and ML/AI ecosystems.
- **Easy to use**
	- Single-service deployment; go from zero to running jobs in minutes.

[![](https://camo.githubusercontent.com/a4d3515f61895cc08a72e92b243441dfc48a91cc83c1590af00e662b3447cc5a/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f64617368626f6172642d707265766965772e706e67)](https://camo.githubusercontent.com/a4d3515f61895cc08a72e92b243441dfc48a91cc83c1590af00e662b3447cc5a/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f64617368626f6172642d707265766965772e706e67)

## 🚀 QuickStart

#### 🐳 Play StreamPark in Docker

```
docker run -d -p 10000:10000 apache/streampark:latest
```

---

#### 🖥️ Local Quick Installation Experience

```
curl -L https://streampark.apache.org/quickstart.sh | sh
```
StreamPark.QuickStart.mp4<video src="https://github.com/user-attachments/assets/dd7d5a89-bc28-4ccc-9ad5-258925fc4f34" controls="controls"></video>

## 🔨 How to Build

```
./build.sh
```

🗄 how to [Development](https://streampark.apache.org/docs/development/development)

## ⬇️ Downloads

Please head to the [releases page](https://streampark.apache.org/download) to download a release of Apache StreamPark.

## 📚 Docs

[Official Documentation](https://streampark.apache.org/docs/get-started)

## 💋 Our users

Various companies and organizations use Apache StreamPark for research, production and commercial products. Are you using this project? [Welcome to add your company](https://github.com/apache/streampark/issues/163)!

[![Our users](https://camo.githubusercontent.com/16d08a09c4d603698996da52e9f46d6c3c0fc8ce30c762627bdc0afde2bdb8d9/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f75736572732e706e673f3230323530323134)](https://camo.githubusercontent.com/16d08a09c4d603698996da52e9f46d6c3c0fc8ce30c762627bdc0afde2bdb8d9/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f75736572732e706e673f3230323530323134)

## 🤝 Contribution

[![PRs Welcome](https://camo.githubusercontent.com/25b3e6d0d42c98de74a98cbb4d149a1c09020cf6d1361993b72d7d5b8ffed363/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f5052732d77656c636f6d652d627269676874677265656e2e7376673f7374796c653d666c61742d737175617265)](https://github.com/apache/streampark/pulls)

### 🙋 Submit Pull Request and Issues

You can submit any ideas as [pull requests](https://github.com/apache/streampark/pulls) or as [issues](https://github.com/apache/streampark/issues/new/choose).

> If you're new to posting issues, we ask that you read [*How To Ask Questions The Smart Way*](http://www.catb.org/~esr/faqs/smart-questions.html) (**This guide does not provide actual support services for this project!**), [How to Report Bugs Effectively](http://www.chiark.greenend.org.uk/~sgtatham/bugs.html) prior to posting. Well written bug reports help us help you!

### 🍻 How to Contribute

We welcome your suggestions, comments (including criticisms), comments and contributions. See [How to Contribute](https://streampark.apache.org/community/submit_guide/submit_code) and [Code Submission Guide](https://streampark.apache.org/community/submit_guide/code_style_and_quality_guide)

Thank you to all the people who already contributed to Apache StreamPark!

## 💬 Contact Us

Contact us through the following mailing list.

| Name | Mailing list |
| --- | --- |
| [dev@streampark.apache.org](mailto:dev@streampark.apache.org) | [Subscribe](mailto:dev-subscribe@streampark.apache.org) 、 [Unsubscribe](mailto:dev-unsubscribe@streampark.apache.org) 、 [Archives](http://mail-archives.apache.org/mod_mbox/streampark-dev/) |

- [X (Twitter)](https://twitter.com/ASFStreamPark)
- [Zhihu](https://www.zhihu.com/people/streampark) (in Chinese)
- [bilibili](https://space.bilibili.com/455330087) (in Chinese)
- WeChat Official Account (in Chinese, scan the QR code to follow)

[![Join the Group](https://camo.githubusercontent.com/ff00546f0a498a1620973bdb049789c1c80705071aa9d214f4a54510325b5442/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f77785f71722e706e67)](https://camo.githubusercontent.com/ff00546f0a498a1620973bdb049789c1c80705071aa9d214f4a54510325b5442/68747470733a2f2f73747265616d7061726b2e6170616368652e6f72672f696d6167652f77785f71722e706e67)  

## 📜 License

Licensed under the [Apache License, Version 2.0](https://github.com/apache/streampark/blob/dev/LICENSE)