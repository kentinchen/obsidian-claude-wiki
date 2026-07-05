---
title: "microsoft/qlib: Qlib is an AI-oriented Quant investment platform that aims to use AI tech to empower Quant Research, from exploring ideas to implementing productions. Qlib supports diverse ML modeling paradigms, including supervised learning, market dynamics modeling, and RL, and is now equipped with https://github.com/microsoft/RD-Agent to automate R&D process."
source: "https://github.com/microsoft/qlib"
author:
published:
created: 2026-04-17
description: "Qlib is an AI-oriented Quant investment platform that aims to use AI tech to empower Quant Research, from exploring ideas to implementing productions. Qlib supports diverse ML modeling paradigms, including supervised learning, market dynamics modeling, and RL, and is now equipped with https://github.com/microsoft/RD-Agent to automate R&D process. - microsoft/qlib"
tags:
  - "clippings"
---
## 📰 What's NEW! 💖

Recent released features

### Introducing: LLM-Based Autonomous Evolving Agents for Industrial Data-Driven R&D

We are excited to announce the release of **RD-Agent** 📢, a powerful tool that supports automated factor mining and model optimization in quant investment R&D.

RD-Agent is now available on [GitHub](https://github.com/microsoft/RD-Agent), and we welcome your star🌟!

To learn more, please visit our [♾️Demo page](https://rdagent.azurewebsites.net/). Here, you will find demo videos in both English and Chinese to help you better understand the scenario and usage of RD-Agent.

We have prepared several demo videos for you:

| Scenario | Demo video (English) | Demo video (中文) |
| --- | --- | --- |
| Quant Factor Mining | [Link](https://rdagent.azurewebsites.net/factor_loop?lang=en) | [Link](https://rdagent.azurewebsites.net/factor_loop?lang=zh) |
| Quant Factor Mining from reports | [Link](https://rdagent.azurewebsites.net/report_factor?lang=en) | [Link](https://rdagent.azurewebsites.net/report_factor?lang=zh) |
| Quant Model Optimization | [Link](https://rdagent.azurewebsites.net/model_loop?lang=en) | [Link](https://rdagent.azurewebsites.net/model_loop?lang=zh) |

- 📃 **Paper**: [R&D-Agent-Quant: A Multi-Agent Framework for Data-Centric Factors and Model Joint Optimization](https://arxiv.org/abs/2505.15155)
- 👾 **Code**: [https://github.com/microsoft/RD-Agent/](https://github.com/microsoft/RD-Agent/)
```
@misc{li2025rdagentquant,
    title={R\&D-Agent-Quant: A Multi-Agent Framework for Data-Centric Factors and Model Joint Optimization},
    ={Yuante Li and Xu Yang and Xiao Yang and Minrui Xu and Xisen Wang and Weiqing Liu and Jiang Bian},
    year={2025},
    eprint={2505.15155},
    archivePrefix={arXiv},
    primaryClass={cs.AI}
}
```

[![image](https://private-user-images.githubusercontent.com/465606/446348319-3198bc10-47ba-4ee0-8a8e-46d5ce44f45d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTcyMTMsIm5iZiI6MTc3NjM1NjkxMywicGF0aCI6Ii80NjU2MDYvNDQ2MzQ4MzE5LTMxOThiYzEwLTQ3YmEtNGVlMC04YThlLTQ2ZDVjZTQ0ZjQ1ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQxNlQxNjI4MzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00NTFhZDNmYTFlNTQzOGE5NzJiYjFmYWFmZGE4OTI1MjdlNzdkYmRiZDNkNGU0OTYzYTRlMDNjNmNlYjZjODBmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.lSTxsARkqhw6nXQ0T6jEVRJEZI9XNIoQ1-4GvpoJKPk)](https://private-user-images.githubusercontent.com/465606/446348319-3198bc10-47ba-4ee0-8a8e-46d5ce44f45d.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzYzNTcyMTMsIm5iZiI6MTc3NjM1NjkxMywicGF0aCI6Ii80NjU2MDYvNDQ2MzQ4MzE5LTMxOThiYzEwLTQ3YmEtNGVlMC04YThlLTQ2ZDVjZTQ0ZjQ1ZC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwNDE2JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDQxNlQxNjI4MzNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00NTFhZDNmYTFlNTQzOGE5NzJiYjFmYWFmZGE4OTI1MjdlNzdkYmRiZDNkNGU0OTYzYTRlMDNjNmNlYjZjODBmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZwbmcifQ.lSTxsARkqhw6nXQ0T6jEVRJEZI9XNIoQ1-4GvpoJKPk)

---

| Feature | Status |
| --- | --- |
| [R&D-Agent-Quant](https://arxiv.org/abs/2505.15155) Published | Apply R&D-Agent to Qlib for quant trading |
| BPQP for End-to-end learning | 📈Coming soon!([Under review](https://github.com/microsoft/qlib/pull/1863)) |
| 🔥LLM-driven Auto Quant Factory🔥 | 🚀 Released in [♾️RD-Agent](https://github.com/microsoft/RD-Agent) on Aug 8, 2024 |
| KRNN and Sandwich models | 📈 [Released](https://github.com/microsoft/qlib/pull/1414/) on May 26, 2023 |
| Release Qlib v0.9.0 | [Released](https://github.com/microsoft/qlib/releases/tag/v0.9.0) on Dec 9, 2022 |
| RL Learning Framework | 🔨 📈 Released on Nov 10, 2022. [#1332](https://github.com/microsoft/qlib/pull/1332), [#1322](https://github.com/microsoft/qlib/pull/1322), [#1316](https://github.com/microsoft/qlib/pull/1316),[#1299](https://github.com/microsoft/qlib/pull/1299),[#1263](https://github.com/microsoft/qlib/pull/1263), [#1244](https://github.com/microsoft/qlib/pull/1244), [#1169](https://github.com/microsoft/qlib/pull/1169), [#1125](https://github.com/microsoft/qlib/pull/1125), [#1076](https://github.com/microsoft/qlib/pull/1076) |
| HIST and IGMTF models | 📈 [Released](https://github.com/microsoft/qlib/pull/1040) on Apr 10, 2022 |
| Qlib [notebook tutorial](https://github.com/microsoft/qlib/tree/main/examples/tutorial) | 📖 [Released](https://github.com/microsoft/qlib/pull/1037) on Apr 7, 2022 |
| Ibovespa index data | 🍚 [Released](https://github.com/microsoft/qlib/pull/990) on Apr 6, 2022 |
| Point-in-Time database | 🔨 [Released](https://github.com/microsoft/qlib/pull/343) on Mar 10, 2022 |
| Arctic Provider Backend & Orderbook data example | 🔨 [Released](https://github.com/microsoft/qlib/pull/744) on Jan 17, 2022 |
| Meta-Learning-based framework & DDG-DA | 📈 🔨 [Released](https://github.com/microsoft/qlib/pull/743) on Jan 10, 2022 |
| Planning-based portfolio optimization | 🔨 [Released](https://github.com/microsoft/qlib/pull/754) on Dec 28, 2021 |
| Release Qlib v0.8.0 | [Released](https://github.com/microsoft/qlib/releases/tag/v0.8.0) on Dec 8, 2021 |
| ADD model | 📈 [Released](https://github.com/microsoft/qlib/pull/704) on Nov 22, 2021 |
| ADARNN model | 📈 [Released](https://github.com/microsoft/qlib/pull/689) on Nov 14, 2021 |
| TCN model | 📈 [Released](https://github.com/microsoft/qlib/pull/668) on Nov 4, 2021 |
| Nested Decision Framework | 🔨 [Released](https://github.com/microsoft/qlib/pull/438) on Oct 1, 2021. [Example](https://github.com/microsoft/qlib/blob/main/examples/nested_decision_execution/workflow.py) and [Doc](https://qlib.readthedocs.io/en/latest/component/highfreq.html) |
| Temporal Routing Adaptor (TRA) | 📈 [Released](https://github.com/microsoft/qlib/pull/531) on July 30, 2021 |
| Transformer & Localformer | 📈 [Released](https://github.com/microsoft/qlib/pull/508) on July 22, 2021 |
| Release Qlib v0.7.0 | [Released](https://github.com/microsoft/qlib/releases/tag/v0.7.0) on July 12, 2021 |
| TCTS Model | 📈 [Released](https://github.com/microsoft/qlib/pull/491) on July 1, 2021 |
| Online serving and automatic model rolling | 🔨 [Released](https://github.com/microsoft/qlib/pull/290) on May 17, 2021 |
| DoubleEnsemble Model | 📈 [Released](https://github.com/microsoft/qlib/pull/286) on Mar 2, 2021 |
| High-frequency data processing example | 🔨 [Released](https://github.com/microsoft/qlib/pull/257) on Feb 5, 2021 |
| High-frequency trading example | 📈 [Part of code released](https://github.com/microsoft/qlib/pull/227) on Jan 28, 2021 |
| High-frequency data(1min) | 🍚 [Released](https://github.com/microsoft/qlib/pull/221) on Jan 27, 2021 |
| Tabnet Model | 📈 [Released](https://github.com/microsoft/qlib/pull/205) on Jan 22, 2021 |

Features released before 2021 are not listed here.

[![](https://github.com/microsoft/qlib/raw/main/docs/_static/img/logo/1.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/logo/1.png)

Qlib is an open-source, AI-oriented quantitative investment platform that aims to realize the potential, empower research, and create value using AI technologies in quantitative investment, from exploring ideas to implementing productions. Qlib supports diverse machine learning modeling paradigms, including supervised learning, market dynamics modeling, and reinforcement learning.

An increasing number of SOTA Quant research works/papers in diverse paradigms are being released in Qlib to collaboratively solve key challenges in quantitative investment. For example, 1) using supervised learning to mine the market's complex non-linear patterns from rich and heterogeneous financial data, 2) modeling the dynamic nature of the financial market using adaptive concept drift technology, and 3) using reinforcement learning to model continuous investment decisions and assist investors in optimizing their trading strategies.

It contains the full ML pipeline of data processing, model training, back-testing; and covers the entire chain of quantitative investment: alpha seeking, risk modeling, portfolio optimization, and order execution. For more details, please refer to our paper ["Qlib: An AI-oriented Quantitative Investment Platform"](https://arxiv.org/abs/2009.11189).

| Frameworks, Tutorial, Data & DevOps | Main Challenges & Solutions in Quant Research |
| --- | --- |
| - [**Plans**](#plans) - [Framework of Qlib](#framework-of-qlib) - [Quick Start](#quick-start) - [Installation](#installation) - [Data Preparation](#data-preparation) - [Auto Quant Research Workflow](#auto-quant-research-workflow) - [Building Customized Quant Research Workflow by Code](#building-customized-quant-research-workflow-by-code) - [**Quant Dataset Zoo**](#quant-dataset-zoo) - [Learning Framework](#learning-framework) - [More About Qlib](#more-about-qlib) - [Offline Mode and Online Mode](#offline-mode-and-online-mode) 	- [Performance of Qlib Data Server](#performance-of-qlib-data-server) - [Related Reports](#related-reports) - [Contact Us](#contact-us) - [Contributing](#contributing) | - - [Forecasting: Finding Valuable Signals/Patterns](#forecasting-finding-valuable-signalspatterns) 		- [**Quant Model (Paper) Zoo**](#quant-model-paper-zoo) 			- [Run a Single Model](#run-a-single-model) 					- [Run Multiple Models](#run-multiple-models) 	- [Adapting to Market Dynamics](#adapting-to-market-dynamics) 	- [Reinforcement Learning: modeling continuous decisions](#reinforcement-learning-modeling-continuous-decisions) |

## Plans

New features under development(order by estimated release time). Your feedbacks about the features are very important.

## Framework of Qlib

[![](https://github.com/microsoft/qlib/raw/main/docs/_static/img/framework-abstract.jpg)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/framework-abstract.jpg)

The high-level framework of Qlib can be found above(users can find the [detailed framework](https://qlib.readthedocs.io/en/latest/introduction/introduction.html#framework) of Qlib's design when getting into nitty gritty). The components are designed as loose-coupled modules, and each component could be used stand-alone.

Qlib provides a strong infrastructure to support Quant research. [Data](https://qlib.readthedocs.io/en/latest/component/data.html) is always an important part. A strong learning framework is designed to support diverse learning paradigms (e.g. [reinforcement learning](https://qlib.readthedocs.io/en/latest/component/rl.html), [supervised learning](https://qlib.readthedocs.io/en/latest/component/workflow.html#model-section)) and patterns at different levels(e.g. [market dynamic modeling](https://qlib.readthedocs.io/en/latest/component/meta.html)). By modeling the market, [trading strategies](https://qlib.readthedocs.io/en/latest/component/strategy.html) will generate trade decisions that will be executed. Multiple trading strategies and executors in different levels or granularities can be [nested to be optimized and run together](https://qlib.readthedocs.io/en/latest/component/highfreq.html). At last, a comprehensive [analysis](https://qlib.readthedocs.io/en/latest/component/report.html) will be provided and the model can be [served online](https://qlib.readthedocs.io/en/latest/component/online.html) in a low cost.

## Quick Start

This quick start guide tries to demonstrate

1. It's very easy to build a complete Quant research workflow and try your ideas with *Qlib*.
2. Though with *public data* and *simple models*, machine learning technologies **work very well** in practical Quant investment.

Here is a quick **[demo](https://terminalizer.com/view/3f24561a4470)** shows how to install `Qlib`, and run LightGBM with `qrun`. **But**, please make sure you have already prepared the data following the [instruction](#data-preparation).

## Installation

This table demonstrates the supported Python version of `Qlib`:

|  | install with pip | install from source | plot |
| --- | --- | --- | --- |
| Python 3.8 | ✔️ | ✔️ | ✔️ |
| Python 3.9 | ✔️ | ✔️ | ✔️ |
| Python 3.10 | ✔️ | ✔️ | ✔️ |
| Python 3.11 | ✔️ | ✔️ | ✔️ |
| Python 3.12 | ✔️ | ✔️ | ✔️ |

**Note**:

1. **Conda** is suggested for managing your Python environment. In some cases, using Python outside of a `conda` environment may result in missing header files, causing the installation failure of certain packages.
2. Please pay attention that installing cython in Python 3.6 will raise some error when installing `Qlib` from source. If users use Python 3.6 on their machines, it is recommended to *upgrade* Python to version 3.8 or higher, or use `conda` 's Python to install `Qlib` from source.

### Install with pip

Users can easily install `Qlib` by pip according to the following command.

```
pip install pyqlib
```

**Note**: pip will install the latest stable qlib. However, the main branch of qlib is in active development. If you want to test the latest scripts or functions in the main branch. Please install qlib with the methods below.

### Install from source

Also, users can install the latest dev version `Qlib` by the source code according to the following steps:

- Before installing `Qlib` from source, users need to install some dependencies:
	```
	pip install numpy
	pip install --upgrade cython
	```
- Clone the repository and install `Qlib` as follows.
	```
	git clone https://github.com/microsoft/qlib.git && cd qlib
	pip install .  # \`pip install -e .[dev]\` is recommended for development. check details in docs/developer/code_standard_and_dev_guide.rst
	```

**Tips**: If you fail to install `Qlib` or run the examples in your environment, comparing your steps and the [CI workflow](https://github.com/microsoft/qlib/blob/main/.github/workflows/test_qlib_from_source.yml) may help you find the problem.

**Tips for Mac**: If you are using Mac with M1, you might encounter issues in building the wheel for LightGBM, which is due to missing dependencies from OpenMP. To solve the problem, install openmp first with `brew install libomp` and then run `pip install .` to build it successfully.

## Data Preparation

❗ Due to more restrict data security policy. The official dataset is disabled temporarily. You can try [this data source](https://github.com/chenditc/investment_data/releases) contributed by the community. Here is an example to download the latest data.

```
wget https://github.com/chenditc/investment_data/releases/latest/download/qlib_bin.tar.gz
mkdir -p ~/.qlib/qlib_data/cn_data
tar -zxvf qlib_bin.tar.gz -C ~/.qlib/qlib_data/cn_data --strip-components=1
rm -f qlib_bin.tar.gz
```

The official dataset below will resume in short future.

---

Load and prepare data by running the following code:

### Get with module

```
# get 1d data
python -m qlib.cli.data qlib_data --target_dir ~/.qlib/qlib_data/cn_data --region cn

# get 1min data
python -m qlib.cli.data qlib_data --target_dir ~/.qlib/qlib_data/cn_data_1min --region cn --interval 1min
```

### Get from source

```
# get 1d data
python scripts/get_data.py qlib_data --target_dir ~/.qlib/qlib_data/cn_data --region cn

# get 1min data
python scripts/get_data.py qlib_data --target_dir ~/.qlib/qlib_data/cn_data_1min --region cn --interval 1min
```

This dataset is created by public data collected by [crawler scripts](https://github.com/microsoft/qlib/blob/main/scripts/data_collector), which have been released in the same repository. Users could create the same dataset with it. [Description of dataset](https://github.com/microsoft/qlib/tree/main/scripts/data_collector#description-of-dataset)

*Please pay **ATTENTION** that the data is collected from [Yahoo Finance](https://finance.yahoo.com/lookup), and the data might not be perfect. We recommend users to prepare their own data if they have a high-quality dataset. For more information, users can refer to the [related document](https://qlib.readthedocs.io/en/latest/component/data.html#converting-csv-format-into-qlib-format)*.

### Automatic update of daily frequency data (from yahoo finance)

> This step is *Optional* if users only want to try their models and strategies on history data.
> 
> It is recommended that users update the data manually once (--trading\_date 2021-05-25) and then set it to update automatically.
> 
> **NOTE**: Users can't incrementally update data based on the offline data provided by Qlib(some fields are removed to reduce the data size). Users should use [yahoo collector](https://github.com/microsoft/qlib/tree/main/scripts/data_collector/yahoo#automatic-update-of-daily-frequency-datafrom-yahoo-finance) to download Yahoo data from scratch and then incrementally update it.
> 
> For more information, please refer to: [yahoo collector](https://github.com/microsoft/qlib/tree/main/scripts/data_collector/yahoo#automatic-update-of-daily-frequency-datafrom-yahoo-finance)

- Automatic update of data to the "qlib" directory each trading day(Linux)
	- use *crontab*: `crontab -e`
		- set up timed tasks:
		```
		* * * * 1-5 python <script path> update_data_to_bin --qlib_data_1d_dir <user data dir>
		```
		- **script path**: *scripts/data\_collector/yahoo/collector.py*
- Manual update of data
	```
	python scripts/data_collector/yahoo/collector.py update_data_to_bin --qlib_data_1d_dir <user data dir> --trading_date <start date> --end_date <end date>
	```
	- *trading\_date*: start of trading day
		- *end\_date*: end of trading day(not included)

### Checking the health of the data

- We provide a script to check the health of the data, you can run the following commands to check whether the data is healthy or not.
	```
	python scripts/check_data_health.py check_data --qlib_dir ~/.qlib/qlib_data/cn_data
	```
- Of course, you can also add some parameters to adjust the test results, such as this.
	```
	python scripts/check_data_health.py check_data --qlib_dir ~/.qlib/qlib_data/cn_data --missing_data_num 30055 --large_step_threshold_volume 94485 --large_step_threshold_price 20
	```
- If you want more information about `check_data_health`, please refer to the [documentation](https://qlib.readthedocs.io/en/latest/component/data.html#checking-the-health-of-the-data).

## Docker images

1. Pulling a docker image from a docker hub repository
	```
	docker pull pyqlib/qlib_image_stable:stable
	```
2. Start a new Docker container
	```
	docker run -it --name <container name> -v <Mounted local directory>:/app pyqlib/qlib_image_stable:stable
	```
3. At this point you are in the docker environment and can run the qlib scripts. An example:
	```
	>>> python scripts/get_data.py qlib_data --name qlib_data_simple --target_dir ~/.qlib/qlib_data/cn_data --interval 1d --region cn
	>>> python qlib/cli/run.py examples/benchmarks/LightGBM/workflow_config_lightgbm_Alpha158.yaml
	```
4. Exit the container
	```
	>>> exit
	```
5. Restart the container
	```
	docker start -i -a <container name>
	```
6. Stop the container
	```
	docker stop <container name>
	```
7. Delete the container
	```
	docker rm <container name>
	```
8. If you want to know more information, please refer to the [documentation](https://qlib.readthedocs.io/en/latest/developer/how_to_build_image.html).

## Auto Quant Research Workflow

Qlib provides a tool named `qrun` to run the whole workflow automatically (including building dataset, training models, backtest and evaluation). You can start an auto quant research workflow and have a graphical reports analysis according to the following steps:

1. Quant Research Workflow: Run `qrun` with lightgbm workflow config ([workflow\_config\_lightgbm\_Alpha158.yaml](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/LightGBM/workflow_config_lightgbm_Alpha158.yaml) as following.
	```
	cd examples  # Avoid running program under the directory contains \`qlib\`
	qrun benchmarks/LightGBM/workflow_config_lightgbm_Alpha158.yaml
	```
	If users want to use `qrun` under debug mode, please use the following command:
	```
	python -m pdb qlib/cli/run.py examples/benchmarks/LightGBM/workflow_config_lightgbm_Alpha158.yaml
	```
	The result of `qrun` is as follows, please refer to [docs](https://qlib.readthedocs.io/en/latest/component/strategy.html#result) for more explanations about the result.
	```
	'The following are analysis results of the excess return without cost.'
	                       risk
	mean               0.000708
	std                0.005626
	annualized_return  0.178316
	information_ratio  1.996555
	max_drawdown      -0.081806
	'The following are analysis results of the excess return with cost.'
	                       risk
	mean               0.000512
	std                0.005626
	annualized_return  0.128982
	information_ratio  1.444287
	max_drawdown      -0.091078
	```
	Here are detailed documents for `qrun` and [workflow](https://qlib.readthedocs.io/en/latest/component/workflow.html).
2. Graphical Reports Analysis: First, run `python -m pip install .[analysis]` to install the required dependencies. Then run `examples/workflow_by_code.ipynb` with `jupyter notebook` to get graphical reports.
	- Forecasting signal (model prediction) analysis
		- Cumulative Return of groups [![Cumulative Return](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/analysis_model_cumulative_return.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/analysis_model_cumulative_return.png)
				- Return distribution [![long_short](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/analysis_model_long_short.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/analysis_model_long_short.png)
				- Information Coefficient (IC) [![Information Coefficient](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/analysis_model_IC.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/analysis_model_IC.png) [![Monthly IC](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/analysis_model_monthly_IC.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/analysis_model_monthly_IC.png) [![IC](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/analysis_model_NDQ.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/analysis_model_NDQ.png)
				- Auto Correlation of forecasting signal (model prediction) [![Auto Correlation](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/analysis_model_auto_correlation.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/analysis_model_auto_correlation.png)
		- Portfolio analysis
		- Backtest return [![Report](https://github.com/microsoft/qlib/raw/main/docs/_static/img/analysis/report.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/analysis/report.png)
		- [Explanation](https://qlib.readthedocs.io/en/latest/component/report.html) of above results

## Building Customized Quant Research Workflow by Code

The automatic workflow may not suit the research workflow of all Quant researchers. To support a flexible Quant research workflow, Qlib also provides a modularized interface to allow researchers to build their own workflow by code. [Here](https://github.com/microsoft/qlib/blob/main/examples/workflow_by_code.ipynb) is a demo for customized Quant research workflow by code.

## Main Challenges & Solutions in Quant Research

Quant investment is a very unique scenario with lots of key challenges to be solved. Currently, Qlib provides some solutions for several of them.

## Forecasting: Finding Valuable Signals/Patterns

Accurate forecasting of the stock price trend is a very important part to construct profitable portfolios. However, huge amount of data with various formats in the financial market which make it challenging to build forecasting models.

An increasing number of SOTA Quant research works/papers, which focus on building forecasting models to mine valuable signals/patterns in complex financial data, are released in `Qlib`

### Quant Model (Paper) Zoo

Here is a list of models built on `Qlib`.

- [GBDT based on XGBoost (Tianqi Chen, et al. KDD 2016)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/XGBoost)
- [GBDT based on LightGBM (Guolin Ke, et al. NIPS 2017)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/LightGBM)
- [GBDT based on Catboost (Liudmila Prokhorenkova, et al. NIPS 2018)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/CatBoost)
- [MLP based on pytorch](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/MLP)
- [LSTM based on pytorch (Sepp Hochreiter, et al. Neural computation 1997)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/LSTM)
- [GRU based on pytorch (Kyunghyun Cho, et al. 2014)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/GRU)
- [ALSTM based on pytorch (Yao Qin, et al. IJCAI 2017)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/ALSTM)
- [GATs based on pytorch (Petar Velickovic, et al. 2017)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/GATs)
- [SFM based on pytorch (Liheng Zhang, et al. KDD 2017)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/SFM)
- [TFT based on tensorflow (Bryan Lim, et al. International Journal of Forecasting 2019)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/TFT)
- [TabNet based on pytorch (Sercan O. Arik, et al. AAAI 2019)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/TabNet)
- [DoubleEnsemble based on LightGBM (Chuheng Zhang, et al. ICDM 2020)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/DoubleEnsemble)
- [TCTS based on pytorch (Xueqing Wu, et al. ICML 2021)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/TCTS)
- [Transformer based on pytorch (Ashish Vaswani, et al. NeurIPS 2017)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/Transformer)
- [Localformer based on pytorch (Juyong Jiang, et al.)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/Localformer)
- [TRA based on pytorch (Hengxu, Dong, et al. KDD 2021)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/TRA)
- [TCN based on pytorch (Shaojie Bai, et al. 2018)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/TCN)
- [ADARNN based on pytorch (YunTao Du, et al. 2021)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/ADARNN)
- [ADD based on pytorch (Hongshun Tang, et al.2020)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/ADD)
- [IGMTF based on pytorch (Wentao Xu, et al.2021)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/IGMTF)
- [HIST based on pytorch (Wentao Xu, et al.2021)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/HIST)
- [KRNN based on pytorch](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/KRNN)
- [Sandwich based on pytorch](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/Sandwich)

Your PR of new Quant models is highly welcomed.

The performance of each model on the `Alpha158` and `Alpha360` datasets can be found [here](https://github.com/microsoft/qlib/blob/main/examples/benchmarks/README.md).

### Run a single model

All the models listed above are runnable with `Qlib`. Users can find the config files we provide and some details about the model through the [benchmarks](https://github.com/microsoft/qlib/blob/main/examples/benchmarks) folder. More information can be retrieved at the model files listed above.

`Qlib` provides three different ways to run a single model, users can pick the one that fits their cases best:

- Users can use the tool `qrun` mentioned above to run a model's workflow based from a config file.
- Users can create a `workflow_by_code` python script based on the [one](https://github.com/microsoft/qlib/blob/main/examples/workflow_by_code.py) listed in the `examples` folder.
- Users can use the script [`run_all_model.py`](https://github.com/microsoft/qlib/blob/main/examples/run_all_model.py) listed in the `examples` folder to run a model. Here is an example of the specific shell command to be used: `python run_all_model.py run --models=lightgbm`, where the `--models` arguments can take any number of models listed above(the available models can be found in [benchmarks](https://github.com/microsoft/qlib/blob/main/examples/benchmarks)). For more use cases, please refer to the file's [docstrings](https://github.com/microsoft/qlib/blob/main/examples/run_all_model.py).
	- **NOTE**: Each baseline has different environment dependencies, please make sure that your python version aligns with the requirements(e.g. TFT only supports Python 3.6~3.7 due to the limitation of `tensorflow==1.15.0`)

### Run multiple models

`Qlib` also provides a script [`run_all_model.py`](https://github.com/microsoft/qlib/blob/main/examples/run_all_model.py) which can run multiple models for several iterations. (**Note**: the script only support *Linux* for now. Other OS will be supported in the future. Besides, it doesn't support parallel running the same model for multiple times as well, and this will be fixed in the future development too.)

The script will create a unique virtual environment for each model, and delete the environments after training. Thus, only experiment results such as `IC` and `backtest` results will be generated and stored.

Here is an example of running all the models for 10 iterations:

```
python run_all_model.py run 10
```

It also provides the API to run specific models at once. For more use cases, please refer to the file's [docstrings](https://github.com/microsoft/qlib/blob/main/examples/run_all_model.py).

### Break change

In `pandas`, `group_key` is one of the parameters of the `groupby` method. From version 1.5 to 2.0 of `pandas`, the default value of `group_key` has been changed from `no default` to `True`, which will cause qlib to report an error during operation. So we set `group_key=False`, but it doesn't guarantee that some programmes will run correctly, including:

- qlib\\examples\\rl\_order\_execution\\scripts\\gen\_training\_orders.py
- qlib\\examples\\benchmarks\\TRA\\src\\dataset.MTSDatasetH.py
- qlib\\examples\\benchmarks\\TFT\\tft.py

## Adapting to Market Dynamics

Due to the non-stationary nature of the environment of the financial market, the data distribution may change in different periods, which makes the performance of models build on training data decays in the future test data. So adapting the forecasting models/strategies to market dynamics is very important to the model/strategies' performance.

Here is a list of solutions built on `Qlib`.

- [Rolling Retraining](https://github.com/microsoft/qlib/blob/main/examples/benchmarks_dynamic/baseline)
- [DDG-DA on pytorch (Wendi, et al. AAAI 2022)](https://github.com/microsoft/qlib/blob/main/examples/benchmarks_dynamic/DDG-DA)

## Reinforcement Learning: modeling continuous decisions

Qlib now supports reinforcement learning, a feature designed to model continuous investment decisions. This functionality assists investors in optimizing their trading strategies by learning from interactions with the environment to maximize some notion of cumulative reward.

Here is a list of solutions built on `Qlib` categorized by scenarios.

### RL for order execution

[Here](https://qlib.readthedocs.io/en/latest/component/rl/overall.html#order-execution) is the introduction of this scenario. All the methods below are compared [here](https://github.com/microsoft/qlib/blob/main/examples/rl_order_execution).

- [TWAP](https://github.com/microsoft/qlib/blob/main/examples/rl_order_execution/exp_configs/backtest_twap.yml)
- [PPO: "An End-to-End Optimal Trade Execution Framework based on Proximal Policy Optimization", IJCAL 2020](https://github.com/microsoft/qlib/blob/main/examples/rl_order_execution/exp_configs/backtest_ppo.yml)
- [OPDS: "Universal Trading for Order Execution with Oracle Policy Distillation", AAAI 2021](https://github.com/microsoft/qlib/blob/main/examples/rl_order_execution/exp_configs/backtest_opds.yml)

## Quant Dataset Zoo

Dataset plays a very important role in Quant. Here is a list of the datasets built on `Qlib`:

| Dataset | US Market | China Market |
| --- | --- | --- |
| [Alpha360](https://github.com/microsoft/qlib/blob/main/qlib/contrib/data/handler.py) | √ | √ |
| [Alpha158](https://github.com/microsoft/qlib/blob/main/qlib/contrib/data/handler.py) | √ | √ |

[Here](https://qlib.readthedocs.io/en/latest/advanced/alpha.html) is a tutorial to build dataset with `Qlib`. Your PR to build new Quant dataset is highly welcomed.

## Learning Framework

Qlib is high customizable and a lot of its components are learnable. The learnable components are instances of `Forecast Model` and `Trading Agent`. They are learned based on the `Learning Framework` layer and then applied to multiple scenarios in `Workflow` layer. The learning framework leverages the `Workflow` layer as well(e.g. sharing `Information Extractor`, creating environments based on `Execution Env`).

Based on learning paradigms, they can be categorized into reinforcement learning and supervised learning.

- For supervised learning, the detailed docs can be found [here](https://qlib.readthedocs.io/en/latest/component/model.html).
- For reinforcement learning, the detailed docs can be found [here](https://qlib.readthedocs.io/en/latest/component/rl.html). Qlib's RL learning framework leverages `Execution Env` in `Workflow` layer to create environments. It's worth noting that `NestedExecutor` is supported as well. This empowers users to optimize different level of strategies/models/agents together (e.g. optimizing an order execution strategy for a specific portfolio management strategy).

## More About Qlib

If you want to have a quick glance at the most frequently used components of qlib, you can try notebooks [here](https://github.com/microsoft/qlib/blob/main/examples/tutorial).

The detailed documents are organized in [docs](https://github.com/microsoft/qlib/blob/main/docs). [Sphinx](http://www.sphinx-doc.org/) and the readthedocs theme is required to build the documentation in html formats.

```
cd docs/
conda install sphinx sphinx_rtd_theme -y
# Otherwise, you can install them with pip
# pip install sphinx sphinx_rtd_theme
make html
```

You can also view the [latest document](http://qlib.readthedocs.io/) online directly.

Qlib is in active and continuing development. Our plan is in the roadmap, which is managed as a [github project](https://github.com/microsoft/qlib/projects/1).

## Offline Mode and Online Mode

The data server of Qlib can either deployed as `Offline` mode or `Online` mode. The default mode is offline mode.

Under `Offline` mode, the data will be deployed locally.

Under `Online` mode, the data will be deployed as a shared data service. The data and their cache will be shared by all the clients. The data retrieval performance is expected to be improved due to a higher rate of cache hits. It will consume less disk space, too. The documents of the online mode can be found in [Qlib-Server](https://qlib-server.readthedocs.io/). The online mode can be deployed automatically with [Azure CLI based scripts](https://qlib-server.readthedocs.io/en/latest/build.html#one-click-deployment-in-azure). The source code of online data server can be found in [Qlib-Server repository](https://github.com/microsoft/qlib-server).

## Performance of Qlib Data Server

The performance of data processing is important to data-driven methods like AI technologies. As an AI-oriented platform, Qlib provides a solution for data storage and data processing. To demonstrate the performance of Qlib data server, we compare it with several other data storage solutions.

We evaluate the performance of several storage solutions by finishing the same task, which creates a dataset (14 features/factors) from the basic OHLCV daily data of a stock market (800 stocks each day from 2007 to 2020). The task involves data queries and processing.

|  | HDF5 | MySQL | MongoDB | InfluxDB | Qlib -E -D | Qlib +E -D | Qlib +E +D |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Total (1CPU) (seconds) | 184.4±3.7 | 365.3±7.5 | 253.6±6.7 | 368.2±3.6 | 147.0±8.8 | 47.6±1.0 | **7.4±0.3** |
| Total (64CPU) (seconds) |  |  |  |  | 8.8±0.6 | **4.2±0.2** |  |

- `+(-)E` indicates with (out) `ExpressionCache`
- `+(-)D` indicates with (out) `DatasetCache`

Most general-purpose databases take too much time to load data. After looking into the underlying implementation, we find that data go through too many layers of interfaces and unnecessary format transformations in general-purpose database solutions. Such overheads greatly slow down the data loading process. Qlib data are stored in a compact format, which is efficient to be combined into arrays for scientific computation.

## Related Reports

- [Guide To Qlib: Microsoft’s AI Investment Platform](https://analyticsindiamag.com/qlib/)
- [微软也搞AI量化平台？还是开源的！](https://mp.weixin.qq.com/s/47bP5YwxfTp2uTHjUBzJQQ)
- [微矿Qlib：业内首个AI量化投资开源平台](https://mp.weixin.qq.com/s/vsJv7lsgjEi-ALYUz4CvtQ)

## Contact Us

- If you have any issues, please create issue [here](https://github.com/microsoft/qlib/issues/new/choose) or send messages in [gitter](https://gitter.im/Microsoft/qlib).
- If you want to make contributions to `Qlib`, please [create pull requests](https://github.com/microsoft/qlib/compare).
- For other reasons, you are welcome to contact us by email([qlib@microsoft.com](mailto:qlib@microsoft.com)).
	- We are recruiting new members(both FTEs and interns), your resumes are welcome!

Join IM discussion groups:

| [Gitter](https://gitter.im/Microsoft/qlib) |
| --- |
| [![image](https://github.com/microsoft/qlib/raw/main/docs/_static/img/qrcode/gitter_qr.png)](https://github.com/microsoft/qlib/blob/main/docs/_static/img/qrcode/gitter_qr.png) |

## Contributing

We appreciate all contributions and thank all the contributors! [![](https://camo.githubusercontent.com/960af5c157693b2096e7a1f11741197ced7fde9054c2b02526fbdb89cbab7906/68747470733a2f2f636f6e747269622e726f636b732f696d6167653f7265706f3d6d6963726f736f66742f716c6962)](https://github.com/microsoft/qlib/graphs/contributors)

Before we released Qlib as an open-source project on Github in Sep 2020, Qlib is an internal project in our group. Unfortunately, the internal commit history is not kept. A lot of members in our group have also contributed a lot to Qlib, which includes Ruihua Wang, Yinda Zhang, Haisu Yu, Shuyu Wang, Bochen Pang, and [Dong Zhou](https://github.com/evanzd/evanzd). Especially thanks to [Dong Zhou](https://github.com/evanzd/evanzd) due to his initial version of Qlib.

## Guidance

This project welcomes contributions and suggestions.  
**Here are some [code standards and development guidance](https://github.com/microsoft/qlib/blob/main/docs/developer/code_standard_and_dev_guide.rst) for submiting a pull request.**

Making contributions is not a hard thing. Solving an issue(maybe just answering a question raised in [issues list](https://github.com/microsoft/qlib/issues) or [gitter](https://gitter.im/Microsoft/qlib)), fixing/issuing a bug, improving the documents and even fixing a typo are important contributions to Qlib.

For example, if you want to contribute to Qlib's document/code, you can follow the steps in the figure below.

[![](https://github.com/demon143/qlib/raw/main/docs/_static/img/change%20doc.gif)](https://github.com/demon143/qlib/blob/main/docs/_static/img/change%20doc.gif)

If you don't know how to start to contribute, you can refer to the following examples.

| Type | Examples |
| --- | --- |
| Solving issues | [Answer a question](https://github.com/microsoft/qlib/issues/749); [issuing](https://github.com/microsoft/qlib/issues/765) or [fixing](https://github.com/microsoft/qlib/pull/792) a bug |
| Docs | [Improve docs quality](https://github.com/microsoft/qlib/pull/797/files); [Fix a typo](https://github.com/microsoft/qlib/pull/774) |
| Feature | Implement a [requested feature](https://github.com/microsoft/qlib/projects) like [this](https://github.com/microsoft/qlib/pull/754); [Refactor interfaces](https://github.com/microsoft/qlib/pull/539/files) |
| Dataset | [Add a dataset](https://github.com/microsoft/qlib/pull/733) |
| Models | [Implement a new model](https://github.com/microsoft/qlib/pull/689), [some instructions to contribute models](https://github.com/microsoft/qlib/tree/main/examples/benchmarks#contributing) |

[Good first issues](https://github.com/microsoft/qlib/labels/good%20first%20issue) are labelled to indicate that they are easy to start your contributions.

You can find some impefect implementation in Qlib by `rg 'TODO|FIXME' qlib`

If you would like to become one of Qlib's maintainers to contribute more (e.g. help merge PR, triage issues), please contact us by email([qlib@microsoft.com](mailto:qlib@microsoft.com)). We are glad to help to upgrade your permission.

## License

Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the right to use your contribution. For details, visit [https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com/).

When you submit a pull request, a CLA bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.