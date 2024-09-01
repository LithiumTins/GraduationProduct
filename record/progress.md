# 进度管理

## 2024.09.01

- 阅读论文《PeriodicSketch: Finding Periodic Items in Data Streams》，精读 Introduction 和 Related Work 部分，大致了解实现和数据结构
  - **解决的问题**：论文提出一种新型的 Sketch，能够在数据流中提取周期性项目
  - **动机**：数据流中的周期性项目有许多的用途，如缓存优化、攻击检测等等。而传统的解决方案耗费的空间和时间都不够理想，偏差也较大，需要一个新的解决方案
  - **解决方案**：结合 Cover-Min Sketch 和 GSU Sketch，替代了大量的布隆过滤器，节约内存，同时支持 O(1) 的插入，并且通过引入概率递增优化精确性
  - **数据结构**：
    - Cover-Min Sketch：和 CM Sketch 相似，一个哈希表数组，每个表中有若干哈希桶，每个桶中记录一个时间戳
    - GSU Sketch：一个哈希表，每个桶为一个数组，每个元素的键为\<项目，时间戳\>，值为计数器
  - **算法**：
    - Cover-Min Sketch：插入时，取映射到的所有时间戳的最小值为上次到来时间，和当前时间计算间隔，传递给 GSU；同时，覆盖所有时间戳
    - GSU Sketch：插入时，以\<项目，时间戳\>映射到一个桶
      - 如果桶中已有该项目，递增计数器
      - 如果桶中没有该项目，以概率替换掉频率最低的项目，并递增计数器

## 2024.08.25

- 阅读 CSDN 文章《论文阅读笔记：A survey of sketches in traffic measurement Design, Optimization, Application》，了解了 Sketch 网络测量的大致架构和工作原理

## 2024.08.11

- 建立项目仓库
- 阅读《基于 Sketch 的网络测量研究与展望》
- 阅读《数据结构知识体系_以及_高级查找表及其分类》
- 下载《PeriodicSketch: Finding Periodic Items in Data Streams（2022 ICDE）》GitHub 仓库并运行代码
