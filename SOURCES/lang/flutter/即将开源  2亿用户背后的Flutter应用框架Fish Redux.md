---
title: "即将开源 | 2亿用户背后的Flutter应用框架Fish Redux"
source: "https://mp.weixin.qq.com/s?__biz=MzU4MDUxOTI5NA==&mid=2247484265&idx=1&sn=ab8aafada4a9e8e0ac4352971569fb77&chksm=fd54d778ca235e6ee5097c57e463f9e62dca367a179b2d5f27bf926ec34e07747d90fae7f785&scene=21#wechat_redirect"
author:
  - "[[吉丰]]"
published:
created: 2026-06-29
description: "面向当下、面向未来的组装式 Flutter 应用框架 Fish Redux。"
tags:
  - "clippings"
---
吉丰 闲鱼技术 *2019年1月16日 17:41*

背景

在闲鱼深度使用 Flutter 开发过程中，我们遇到了业务代码耦合严重，代码可维护性糟糕，如入泥泞。对于闲鱼这样的负责业务场景，我们需要一个统一的应用框架来摆脱当下的开发困境，而这也是 Flutter 领域空缺的一块处女地。

Fish Redux 是为解决上面问题上层应用框架，它是一个基于 Redux 数据管理的组装式 flutter 应用框架， 特别适用于构建中大型的复杂应用。

它的最大特点是配置式组装， 它会非常干净，易编写、易维护、易协作。

Fish Redux 的灵感主要来自于 Redux、React、Elm、Dva 这样的优秀框架，而 Fish Redux 站在巨人的肩膀上，将集中，分治，复用，隔离做的更进一步。

分层架构图

架构图，主体自底而上，分三层，每一层用来解决不同层面的问题和矛盾，下面依次来展开。

Redux

- Redux 是来自前端社区的一个数据管理框架， 对 Native 开发同学来说可能会有一点陌生，我们做一个简单的介绍。

1

**Redux做什么的？**

- Redux 是一个用来做\[可预测\]\[集中式\]\[易调试\]\[灵活性\]的数据管理的框架。所有对数据的增删改查等操作都由 Redux 来集中负责。

2

**Redux是怎么设计和实现的？**

- Redux 是一个函数式的数据管理的框架。 传统 OOP 做数据管理，往往是定义一些 Bean，每一个 Bean 对外暴露一些 Public-API 用来操作内部数据（充血模型）。 函数式的做法是更上一个抽象的纬度，对数据的定义是一些 Struct（贫血模型），而操作数据的方法都统一到具有相同函数签名 (T, Action) => T 的 Reducer 中。 FP:Struct（贫血模型） + Reducer = OOP:Bean（充血模型） 同时 Redux 加上了 FP 中常用的 Middleware（AOP） 模式和 Subscribe 机制，给框架带了极高的灵活性和扩展性。 贫血模型、充血模型 参考： https://en.wikipedia.org/wiki/PlainoldJava\_object

3

**Redux的缺点？**

- Redux 核心仅仅关心数据管理，不关心具体什么场景来使用它，这是它的优点同时也是它的缺点。
- 在我们实际使用 Redux 中面临两个具体问题
- Redux 的集中和 Component 的分治之间的矛盾。
	- Redux 的 Reducer 需要一层层手动组装，带来的繁琐性和易错性。

4

**Fish Redux的改良？**

Fish Redux 通过 Redux 做集中化的可观察的数据管理。然不仅于此，对于传统 Redux 在使用层面上的缺点，在面向端侧 flutter 页面纬度开发的场景中，我们通过更好更高的抽象，做了改良。

一个组件需要定义一个数据（Struct）和一个 Reducer。同时组件之间存在着父依赖子的关系。通过这层依赖关系，我们解决了【集中】和【分治】之间的矛盾，同时对 Reducer 的手动层层 Combine 变成由框架自动完成，大大简化了使用 Redux 的困难。

我们得到了理想的集中的效果和分治的代码。

5

**对社区标准的follow**

- State、Action、Reducer、Store、Middleware 以上概念和社区的 ReduxJS 是完全一致的。我们将原汁原味地保留所有的 Redux 的优势。
- 如果想对 Redux 有更近一步的理解，请参考 https://github.com/reduxjs/redux

Component

组件是对局部的展示和功能的封装。 基于 Redux 的原则，我们对功能细分为修改数据的功能(Reducer)和非修改数据的功能(副作用 Effect)。

于是我们得到了，View、 Effect、Reducer 三部分，称之为组件的三要素，分别负责了组件的展示、非修改数据的行为、修改数据的行为。

这是一种面向当下，也面向未来的拆分。在面向当下的 Redux 看来，是数据管理和其他。在面向未来的 UI-Automation 看来是 UI 表达和其他。

UI 的表达对程序员而言即将进入黑盒时代，研发工程师们会把更多的精力放在非修改数据的行为、修改数据的行为上。

组件是对视图的分治，也是对数据的分治。通过逐层分治，我们将复杂的页面和数据切分为相互独立的小模块。这将利于团队内的协作开发。

1

**关于View**

View 仅仅是一个函数签名: (T,Dispatch,ViewService) => Widget

它主要包含三方面的信息：

- 视图是完全由数据驱动。
- 视图产生的事件／回调，通过 Dispatch 发出“意图”，不做具体的实现。
- 需要用到的组件依赖等，通过 ViewService 标准化调用。 比如一个典型的符合 View 签名的函数

2

**关于Effect**

Effect 是对非修改数据行为的标准定义，它是一个函数签名: (Context, Action) => Object

它主要包含四方面的信息：

- 接收来自 View 的“意图”，也包括对应的生命周期的回调，然后做出具体的执行。
- 它的处理可能是一个异步函数，数据可能在过程中被修改，所以我们不崇尚持有数据，而通过上下文来获取最新数据。
- 它不修改数据， 如果修要，应该发一个 Action 到 Reducer 里去处理。
- 它的返回值仅限于 bool or Future， 对应支持同步函数和协程的处理流程。 比如：良好的协程的支持

3

**关于Reducer**

Reducer 是一个完全符合 Redux 规范的函数签名:(T,Action) => T

一个符合签名的 Reducer

同时我们以显式配置的方式来完成大组件所依赖的小组件、适配器的注册，这份依赖配置称之为 Dependencies。

所以有这样的公式 Component = View + Effect(可选) + Reducer(可选) + Dependencies(可选)。

一个典型的组装

通过 Component 的抽象，我们得到了完整的分治，多纬度的复用，更好的解耦。

Adapter

Adapter 也是对局部的展示和功能的封装。它为 ListView 高性能场景而生，它是 Component 实现上的一种变化。

- 它的目标是解决 Component 模型在 flutter-ListView 的场景下的 3 个问题
- 1）将一个"Big-Cell"放在 Component 里，无法享受 ListView 代码的性能优化。
	- 2）Component 无法区分 appear|disappear 和 init|dispose 。
	- 3）Effect 的生命周期和 View 的耦合，在 ListView 的场景下不符合直观的预期。 概括的讲，我们想要一个逻辑上的 ScrollView，性能上的 ListView ，这样的一种局部展示和功能封装的抽象。 做出这样独立一层的抽象是， 我们看实际的效果， 我们对页面不使用框架，使用框架 Component，使用框架 Component+Adapter 的性能基线对比
- Reducer is long-lived, Effect is medium-lived, View is short-lived. 我们通过不断的测试做对比，以某 android 机为例：
- 使用框架前 我们的详情页面的 FPS，基线在 52FPS。
- 使用框架， 仅使用 Component 抽象下，FPS 下降到 40， 遭遇“Big-Cell”的陷阱。
- 使用框架，同时使用 Adapter 抽象后，FPS 提升到 53，回到基线以上，有小幅度的提升。

Dictionary

推荐的目录结构会是这样

```
sample_page-- action.dart-- page.dart-- view.dart-- effect.dart-- reducer.dart-- state.dartcomponentssample_component-- action.dart-- component.dart-- view.dart-- effect.dart-- reducer.dart-- state.dart
```

上层负责组装，下层负责实现, 同时会有一个插件提供， 便于我们快速填写。

以闲鱼的详情场景为例的组装：

组件和组件之间，组件和容器之间都完全的独立。

Communication Mechanism

- 组件|适配器内通信
- 组件|适配器间内通信

简单的描述：采用的是带有一段优先处理的广播， self-first-broadcast。 发出的 Action，自己优先处理，否则广播给其他组件和 Redux 处理。 最终我们通过一个简单而直观的 dispatch 完成了组件内，组件间（父到子，子到父，兄弟间等）的所有的通信诉求。

Refresh Mechanism

1

**数据刷新**

- 局部数据修改，自动层层触发上层数据的浅拷贝，对上层业务代码是透明的。
- 层层的数据的拷贝
- 一方面是对 Redux 数据修改的严格的 follow。
	- 另一方面也是对数据驱动展示的严格的 follow。

2

**视图刷新**

- 扁平化通知到所有组件，组件通过 shouldUpdate 确定自己是否需要刷新

优点

1

**数据的集中管理**

- 通过 Redux 做集中化的可观察的数据管理。我们将原汁原味地保留所有的 Redux 的优势，同时在 Reducer 的合并上，变成由框架代理自动完成，大大简化了使用 Redux 的繁琐度。

2

**组件的分治管理**

- 组件既是对视图的分治，也是对数据的分治。通过逐层分治，我们将复杂的页面和数据切分为相互独立的小模块。这将利于团队内的协作开发。

3

**View、Effect、Reducer隔离**

- 将组件拆分成三个无状态的互不依赖的函数。因为是无状态的函数，它更易于编写、调试、测试、维护。同时它带来了更多的组合、复用和创新的可能。

4

声明式配置组装

- 组件、适配器通过自由的声明式配置组装来完成。包括它的 View、Reducer、Effect 以及它所依赖的子项。

5

良好的扩展性

- 核心框架保持自己的核心的三层关注点，不做核心关注点以外的事情，同时对上层保持了灵活的扩展性。
- 框架甚至没有任何的一行的打印的代码，但我们可通过标准的 Middleware 来观察到数据的流动，组件的变化。
	- 在框架的核心三层外，也可以通过 dart 的语言特性 为 Component 或者 Adapter 添加 mixin，来灵活的组合式地增强他们的上层使用上的定制和能力。
	- 框架和其他中间件的打通，诸如自动曝光、高可用等，各中间件和框架之间都是透明的，由上层自由组装。

6

精小、简单、完备

- 它非常小，仅仅包含 1000 多行代码。
- 它使用简单，完成几个小的函数，完成组装，即可运行。
- 它是完备的。

**Fish Redux 目前已在阿里巴巴闲鱼技术团队内多场景，深入应用。 Talk is cheap, Show me the code，我们即将开源，敬请关注公众号。**

![图片](https://mmbiz.qpic.cn/mmbiz_gif/DUwiayJ0Mj1FNHKnudFye1UH5c6rOUmicIaaajGB69WvufvcmPacOPiaettBvyPBYt4HIHH7KsmFh3Y9tEHzHoXdQ/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=28)

[深度｜10分钟读懂阿里巴巴高级专家在Flutter Live2018的分享](http://mp.weixin.qq.com/s?__biz=MzU4MDUxOTI5NA==&mid=2247484184&idx=1&sn=441f4c53d42c742eaba2edce679ef9d1&chksm=fd54d709ca235e1f9507b63916fad95086f86d6e87cbd8d02c2bfe6431bcce04ee0b361ed13e&scene=21#wechat_redirect)

[谷歌开发者大会2018·TensorFlow应用“UI 2 Code"](http://mp.weixin.qq.com/s?__biz=MzU4MDUxOTI5NA==&mid=2247484015&idx=1&sn=4f6c12ebc8da2d95085c10da9d12feb9&chksm=fd54d67eca235f6843dbd08a470a5506a08e79bb9cf56038e129cc2830a0a95b6cf6a4cd821f&scene=21#wechat_redirect)

[千人千面线上问题回放技术揭秘](http://mp.weixin.qq.com/s?__biz=MzU4MDUxOTI5NA==&mid=2247484030&idx=1&sn=30c4df5705d1da8d8c84c4aa1ac7dcc4&chksm=fd54d66fca235f795e92af0edda51f3776a99c4f1526b1d872c447d6504b0fa213dd1bca957c&scene=21#wechat_redirect)

[2018双11·尖货优品实时选——“马赫”](http://mp.weixin.qq.com/s?__biz=MzU4MDUxOTI5NA==&mid=2247484101&idx=1&sn=2ff09963e0afb1a605334eefa54b3377&chksm=fd54d6d4ca235fc2eb0373b85dfa9c9f6dd587f0e5c729c0a31f58a8b6553a0d5e365794f635&scene=21#wechat_redirect)

![图片](https://mmbiz.qpic.cn/mmbiz_png/DUwiayJ0Mj1GibVUaHI1w5nWC9WGf5dvLU0XFQ0boytaDXhpVHfoGiahtqQJjSAhak3Q6wPRPYibRfxvv8iafBRIVZg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1#imgIndex=29)

闲鱼Flutter · 目录