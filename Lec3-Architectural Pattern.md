Lec3-Architectural Pattern
---
1. 架构模式是一组架构设计决策，适用于重复出现的设计问题，并进行了参数化处理以解决出现该问题的不同软件开发环境。An architectural pattern is a set of architectural design decisions that are applicable to a recurring design problem, and parameterized to account for different software development contexts in which that problem appears.
2. 体系结构模式与DSSA相似，但适用于较低级别，范围更窄。Architectural patterns are similar to I SSAs but applied at a lower level" and within a much narrower scope.

![](img/lec3/1.png)

# 1. 领域特定的软件体系结构 Domain-Specific Software Architecture
1. 领域特定的软件体系结构(DSSA)是软件组件的组合 Domain- Specific Software Architectures (DSSA) isan assemblage ot sottware components
   1. 专用于特定类型的任务(域) specialized for a particular type of task (domain) generalized for effective use across that domain, and
   2. 普遍适用于该领域的有效使用 composed in a standardized structure (topology)
   3. 有效构建成功应用程序的标准化结构(拓扑)组成 effective for building successful applications.
2. DSSA是最大限度地重用知识和进行先期开发并因此开发新的体系结构设计的卓越手段。DSSAs are the pre-eminent means for maximal reuse of knowledge and prior development and hence for developing a new architectural design.

# 2. (程序)设计模式 (Program) Design Patterns

## 2.1. 架构模式 Architectural Patterns
1. 架构模式 Architecture pattern
   1. 是在实践中**反复**发现的一揽子设计决策 is a package of design decisions that is found repeatedly in practice,
   2. 具有允许**重复使用**的已知属性，并且描述了**一类**架构 has known properties that permit reuse, and describes a class of architectures.
2. 架构模式建立了以下之间的**关系**：Architecture pattern establishes a relationship between:
   1. **背景**：世界上经常发生的常见问题，会引起问题 A context: A recurring, common situation in the world that gives rise to a problem.
   2. 一个**问题**：在给定的上下文中出现的问题，经过适当概括 A problem: The problem, appropriately generalized, that arises in the given context.
   3. **解决方案**：针对问题的成功架构解决方案，并进行了适当抽象 A solution: A successful architecture resolution to the problem, appropriately abstracted. 
3. 在实践中找到模式 Patterns are found in practice
   1. 一个人不发明模式，一个人发现它们 One does not invent patterns, one discovers them
   2. 永远不会有一个**完整的模式列表** There will never be a complete list of patterns

## 2.2. 分层模式 Layered Pattern

### 2.2.1. 解决方案
![](img/lec3/2.png)

### 2.2.2. 堆栈符号
![](img/lec3/3.png)

### 2.2.3. 基于分层模式的系统
![](img/lec3/4.png)

### 2.2.4. 分层模式变体
![](img/lec3/5.png)

## 2.3. 代理模式 Broker Pattern

### 2.3.1. 解决方案
![](img/lec3/6.png)

### 2.3.2. 概述图
![](img/lec3/7.png)

## 2.4. 模型-视图-控制器模式 Model-View-Controller Pattern(MVC)

### 2.4.1. 解决方案
![](img/lec3/8.png)

### 2.4.2. 概述图
![](img/lec3/9.png)

## 2.5. Pipe-and-Filter Pattern 管道和过滤模式

### 2.5.1. 解决方案
![](img/lec3/10.png)

### 2.5.2. 概述图
![](img/lec3/11.png)

## 2.6. Client-Server Pattern 客户端-服务端模式

### 2.6.1. 解决方案
![](img/lec3/12.png)

### 2.6.2. 概述图
![](img/lec3/13.png)

## 2.7. Peer-to-Peer Pattern 点对点模式

### 2.7.1. 解决方案
![](img/lec3/14.png)

### 2.7.2. 概述图
![](img/lec3/15.png)

## 2.8. Service-Oriented Pattern 面向服务的模式

### 2.8.1. 解决方案
![](img/lec3/16.png)

### 2.8.2. 概述图
![](img/lec3/17.png)

### 2.8.3. SOA中的连接器
1. **SOAP**(简单对象访问协议)：服务使用者和提供者通过通常在**HTTP之上**交换请求/答复**XML消息**进行交互 SOAP (Simple Object Access Protocol): Service consumers and providers interact by exchanging request/reply XML messages typically on top of HTTP
2. **REST**(代表性状态传输)：服务使用者发送依赖于**四个**基本**HTTP命令(POST，GET，PUT，DELETE)**的HTTP请求REST (Representational State Transfer) : A service consumer sends HT TP requests that rely on; four basic HTTP commands (POST, GET, PUT, DELETE)
3. **异步消息传递**(“**即发即忘**”)：参与者不必等待收据的确认。Asynchronous messaging ("fire-and-forget"): Participants do not have to wait for an acknowledgment of receipt.

## 2.9. Publish-Subscribe Pattern 发布-订阅模式

### 2.9.1. 解决方案
![](img/lec3/18.png)

### 2.9.2. 概述图
![](img/lec3/19.png)

## 2.10. Shared-Data Pattern 共享数据模式3

### 2.10.1. 解决方案
![](img/lec3/21.png)

### 2.10.2. 概述图
![](img/lec3/20.png)

## 2.11. Map-Reduce Pattern

### 2.11.1. 解决方案
![](img/lec3/22.png)

### 2.11.2. 概述图
![](img/lec3/23.png)

## 2.12. Multi-Tier Pattern 多层模式

### 2.12.1. 解决方案
![](img/lec3/24.png)

### 2.12.2. 概述图
![](img/lec3/25.png)

# 3. 模式与策略 Architecture Putterns and Tactics
1. 策略比模式简单。他们使用**单一的结构或机制**来应对**单一的架构力量** Tactics are simpler than patterns; they use a single structure or mechanism to address a single architectural force.
2. 模式通常将多个设计决策组合到一个包中 Patterns typically combine multiple design decisions into a package.
3. 模式和策略共同构成了软件设计师的主要工具 Patterns and tactics together constitute the software architect' s primary tools.
4. **战术是设计的“构建块”**，可从中创建建筑模式 Tactics are "building blocks" of design from which architectural patterns are created.
5. 大多数模式包含几种不同的策略，这些策略可能 Most patterns consist of several different tactics that may:
   1. 都有共同的目的 all serve a common purpose,
   2. 经常被选择来承诺不同的质量属性 be often chosen to promise different quality attributes
6. 示例：分层图案 Example: layered pattern
   1. 提高语义连贯性 Increase semantic coherence
   2. 限制依赖 Restrict dependencies

![](img/lec3/26.png)

![](img/lec3/27.png)

| ![](img/lec3/28.png) | ![](img/lec3/29.png) |
| -------------------- | -------------------- |
| ![](img/lec3/30.png) | ![](img/lec3/31.png) |

# 4. Reading Materials
![](img/lec3/32.png)
