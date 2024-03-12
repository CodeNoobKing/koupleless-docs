---
title: Introduction and Use Cases
date: 2024-01-25T10:28:32+08:00
description: Introduction to Koupleless and its Use Cases
weight: 100
---

# Introduction
Koupleless is a modular Serverless technology solution that enables ordinary applications to evolve into Serverless development mode at a relatively low cost, allowing code and resources to be decoupled and easily maintained independently. At the same time, it supports capabilities such as second-level build deployment, merged deployment, and dynamic scalability, providing users with the ultimate development and operation experience, ultimately helping enterprises achieve cost reduction and efficiency improvement. With the increasing digital transformation across various industries, enterprises are facing more and more pain points in terms of development efficiency, collaboration efficiency, resource costs, and service governance. Let's explore these pain points one by one and see how they are addressed in Koupleless.

# Use Cases

## Pain Point 1: Slow Application Build and Deployment or Tedious SDK Upgrades
Traditional application image building usually takes 3-5 minutes, and deploying code to start completion also takes 3-5 minutes. Developers have to undergo **multiple 6-10 minute** build and deployment waits each time they verify or deploy code changes, severely impacting development efficiency. Additionally, each SDK upgrade (such as middleware frameworks, RPC, logging, JSON, etc.) requires modifying all application code and re-building and deploying, causing unnecessary disruption to developers. <br /> By using **Koupleless** **Universal Base** and accompanying tools, you can cost-effectively split applications into "**base**" and "**module**". The base encapsulates common SDKs of the company or a specific business department, and base upgrades can be handled by specialists without affecting business developers, who only need to write modules. In our currently supported Java technology stack, a module is a SpringBoot application code package (FatJar). However, the SpringBoot framework itself and other enterprise dependencies are pre-loaded and warmed up by the base at runtime. Each time a module is deployed, it finds a base with pre-heated SpringBoot for hot deployment, similar to AppEngine, enabling users to achieve **10-second build and deployment** for applications and **seamless SDK upgrades**.

<img width="800px" alt="应用构建发布速度" src="https://intranetproxy.alipay.com/skylark/lark/0/2023/png/671/1694592240984-8ea49823-ebd0-4bb7-909c-380f0439382b.png#clientId=u0d56718b-4144-4&from=paste&height=164&id=uab4fd245&originHeight=328&originWidth=2350&originalType=binary&ratio=2&rotation=0&showTitle=false&size=259703&status=done&style=none&taskId=u4aa5d723-f988-41e6-86fc-8c08d59e517&title=&width=1175" />

## Pain Point 2: High Resource Costs for Long-tail Applications
In enterprises, 80% of applications serve less than 20% of the traffic. Along with business changes, enterprises have many **long-tail applications**. These long-tail applications have CPU utilization rates of less than 10% for an extended period, leading to significant **resource waste**. <br />By using **Koupleless** **merged deployment** and accompanying tools, you can cost-effectively achieve the merged deployment of multiple applications, solving the problem of excessive fragmentation of enterprise applications and the resource waste caused by low-traffic businesses, thus **saving costs**. <br />
<img width="700px" alt="应用机器成本" src="https://intranetproxy.alipay.com/skylark/lark/0/2023/png/671/1694593117757-d2932c29-c4c2-4ecc-9a41-59a750d53823.png#clientId=u0d56718b-4144-4&from=paste&height=132&id=u349c574f&originHeight=318&originWidth=1382&originalType=binary&ratio=2&rotation=0&showTitle=false&size=158864&status=done&style=none&taskId=u1389af9d-06db-468f-810a-09bc615b751&title=&width=574" /><br />
Here, "Business A Application 1" is called a "module" in Koupleless terminology. Multiple module applications can be merged into the same base using SOFAArk technology. The base can be a completely empty SpringBoot application (Java technology stack), or it can sink some common SDKs to the base. Each time a module application is deployed, it restarts the base machine. In this way, module applications maximize the reuse of the base's **memory** (Metaspace and Heap), reduce the size of build artifacts from **hundreds of MB** to **tens of MB** or even more aggressively, and effectively improve **CPU usage**.

## Pain Point 3: Low Collaboration Efficiency in Enterprise R&D
In enterprises, some applications require **multi-person development** collaboration. In the traditional development mode, each person's code change requires the entire application to be released, leading to a **fire-fighting** approach to application development iteration. Everyone needs to develop iteratively within a unified time window and release online at a unified time, resulting in a large number of demand release **waits**, environment machine **preemptions**, iteration **conflicts**, and other situations. <br /> By using **Koupleless**, you can easily split applications into a **base** and multiple functional **modules**, where each functional module is a group of code files. Different functional modules can be developed and deployed iteratively **simultaneously**, and they are **independent of each other**, eliminating the traditional application iteration **fire-fighting** approach. Each module has its independent iteration, greatly improving the **efficiency of demand delivery**. If you enable **hot deployment** for modules (or restart the entire base each time a module is deployed), the single build + deployment time for modules will also be reduced from **6-10 minutes** of normal applications to seconds.
<img width="800px" alt="协作效率低" src="https://intranetproxy.alipay.com/skylark/lark/0/2023/png/671/1694594675815-3037ffe1-2048-4c86-bc50-456697b197d5.png#clientId=u0d56718b-4144-4&from=paste&height=552&id=u36ac4b83&originHeight=1066&originWidth=1154&originalType=binary&ratio=2&rotation=0&showTitle=false&size=428189&status=done&style=none&taskId=u7fc53ae9-ff48-4ae5-a821-44dbee64aaa&title=&width=598" />

## Pain Point 4: Difficulties in Accumulating Business Assets to Improve Middle Platform Efficiency
In some medium and large enterprises, various **business middle platforms** are accumulated. Middle platforms generally encapsulate the common API implementation and **SPI** definitions of the business. The SPI definition allows plugins on the middle platform to implement their own business logic. After the traffic enters the middle platform application, it calls the corresponding SPI implementation component to complete the corresponding business logic. Components in the middle platform application have relatively simple business logic. Deploying them as independent applications will incur high **resource and operation costs** and slow **build and deployment speeds**, significantly increasing the development burden and affecting development efficiency. <br /> With Koupleless, you can easily split the middle platform application into a **base** and multiple functional **modules**. The base can accumulate relatively thick business dependencies, common logic, API implementations, SPI definitions, etc. (referred to as business assets), and provide them to the modules above. The modules can use the capabilities of the base through direct calls between objects or beans, with almost no code modification. Moreover, multiple modules can be developed and deployed iteratively **simultaneously** without **affecting each other**, greatly improving **collaborative delivery efficiency**. Additionally, for relatively simple modules, you can also enable hot deployment, and the single build + deployment time will be reduced from **6-10 minutes** of normal applications to within **30 seconds**.
<img width="800px" alt="提高中台效率" src="https://intranetproxy.alipay.com/skylark/lark/0/2023/png/671/1694601773808-b25f5beb-a4e4-4d93-ba55-6f61bf0377bc.png#clientId=u2162a7aa-3111-4&from=paste&height=386&id=uf98e4ae9&originHeight=1016&originWidth=1400&originalType=binary&ratio=2&rotation=0&showTitle=false&size=470581&status=done&style=none&taskId=u44970d8c-1234-447f-bbb6-ceea4a44cfc&title=&width=532" />

## Pain Point 5: High Cost of Microservice Evolution
Different businesses in enterprises have different development stages, so applications also have their own lifecycles.

**Startup Phase**: A startup application generally adopts a **monolithic architecture**.<br />↓<br />**Growth Phase**: As the business grows, the number of application developers also increases. At this time, you may be **uncertain** about the future prospects of the business and do not want to split the business into multiple applications prematurely to avoid unnecessary **maintenance, governance, and resource costs**. Therefore, you can use **Koupleless** to cost-effectively split the application into a base and multiple functional modules, allowing different functional modules to be developed, operated, and iterated independently in parallel, thus improving the **collaboration and demand delivery** efficiency of the application in this stage. <br />↓<br />**Mature Phase**: As the business further expands, you can use Koupleless to cost-effectively split some or all functional modules into independent applications for development and operation. <br />↓<br />**Long-tail Phase**: Some businesses may gradually enter a low-activity or long-tail phase after experiencing growth or maturity phases. At this time, you can use Koupleless to **easily convert** these applications into modules, **merge** them, and **deploy** them together to achieve **cost reduction and efficiency improvement**.

It can be seen that **Koupleless** supports enterprises to smoothly transition between the startup, growth, mature, and long-tail phases of applications at a low cost and even switch back and forth, thereby easily keeping the application architecture synchronized with business development. <br /> Application lifecycle evolution.
<img width="1200px" alt="微服务演进成本" src="https://intranetproxy.alipay.com/skylark/lark/0/2023/png/671/1694602307402-510d44ec-314c-44c4-96d8-bb978dd027ff.png#clientId=u2162a7aa-3111-4&from=paste&height=217&id=u8b5b547c&originHeight=434&originWidth=2458&originalType=binary&ratio=2&rotation=0&showTitle=false&size=266126&status=done&style=none&taskId=u09776530-0a41-4081-be17-c42db50e8b1&title=&width=1229" />

<br/>
<br/>