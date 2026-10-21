# 合同审查

用模型定位条款，用规则给合同风险分级，并留下可核对的审查记录。

本仓库是 [moonligh](https://moonligh.cn/) 的个人开源项目，采用 [Apache-2.0](LICENSE) 许可证。

## 概述

模型负责定位条款并抽出实体，规则负责风险分级和红线判定。审查分成三个独立接口：规则判定、条款修订、签核。每一步记录执行阶段、引用的产物和内容哈希，方便事后核对有没有被改过。

规则使用仓库自带的示例集，可以整份替换。真实客户合同不进入仓库。

## 状态

当前提交的是仓库骨架和社区文件。包名、目录和文档已经按开源仓库放好，业务代码和构建文件尚未写入。下面的功能范围是这个仓库要完成的事，还不是已经可运行的能力。

## 功能范围

- 定位条款并抽取主体、期限、金额等实体
- 按示例规则完成高、中、低分级和红线判定
- 把规则判定、条款修订、签核拆成三个接口
- 记录执行阶段、引用产物和内容哈希

## 技术选择

五个仓库使用同一套运行时，模型接入使用 Spring AI。

- JDK 21
- Spring Boot 4.1.1
- Spring AI 2.0.1
- MySQL 8.0.46
- Redis 8.2.10
- RocketMQ 5.5.1，Java 客户端使用 rocketmq-spring 2.3.6

在本仓库中，Spring AI 负责定位条款和抽取实体，规则引擎负责分级和红线。MySQL 保存执行阶段、引用产物和内容哈希。三个阶段通过独立接口衔接。

源码目录按 Maven 标准布局预留。构建文件会和第一批可运行代码一起提交。

## 目录

```text
src/main/java/com/moonligh/contract/
src/main/resources/
src/test/java/com/moonligh/contract/
```

Java 包名是 `com.moonligh.contract`。

## 数据

示例合同和规则由仓库自带。真实客户合同、成交文本和内部审查标准不进入仓库。

## 路线图

- [ ] 定位条款并抽取主体、期限、金额等实体
- [ ] 按示例规则完成高、中、低分级和红线判定
- [ ] 把规则判定、条款修订、签核拆成三个接口
- [ ] 记录执行阶段、引用产物和内容哈希
- [ ] 补齐构建文件、启动入口和示例
- [ ] 为核心路径补测试

## 声明

本项目提供的是合同信息整理，不能替代律师审查或正式法律意见。

## 系列仓库

- `registration-assistant`：导诊挂号助手
- `report-interpreter`：报告解读
- `nutritionist`：饮食方案
- `case-analysis`：案情分析

## 参与贡献

贡献方式见 [CONTRIBUTING.md](CONTRIBUTING.md)，行为准则见 [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)。安全问题见 [SECURITY.md](SECURITY.md)，请不要把漏洞细节写进公开 Issue。

## 许可证

Copyright 2026 moonligh

本项目使用 Apache License 2.0，全文见 [LICENSE](LICENSE)。
