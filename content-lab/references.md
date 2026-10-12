# 公开方法与工具参考

研究日期：2026-10-12。仅检查一手文档、部分关键代码及公开运行记录，未安装、登录、部署或做运行时测试。以下区分“借鉴的方法”与“尚未验证的工具能力”；仓库存在、功能自述或测试通过都不等于适合直接投入使用。

## 优先借鉴的方法

### 1. LangChain social-media-agent：人工审阅与编辑反馈

[项目说明](https://github.com/langchain-ai/social-media-agent/blob/main/README.md) 与 [生成流程代码](https://github.com/langchain-ai/social-media-agent/blob/main/src/agents/generate-post/generate-post-graph.ts) 展示了生成、人工审阅、重写、再次确认及排程的分支。

[反思节点](https://github.com/langchain-ai/social-media-agent/blob/main/src/agents/reflection/index.ts) 根据明确的用户编辑反馈更新写作提示，并要求不要从隐含反馈过度概括。值得借鉴的是保存“改了什么、为什么改、适用范围”。这类编辑反馈不是发布后的平台表现，不能证明流量效果。

该节点会把原稿与反馈发给外部 LangMem 服务；采用前须核对接收方、内容范围、权限与隐私。公开记录显示 [10 月 11 日集成测试失败](https://github.com/langchain-ai/social-media-agent/actions/runs/38148314189)，同类任务在 10 月 7—11 日均失败；[10 月 12 日 CI](https://github.com/langchain-ai/social-media-agent/actions/runs/38256407774) 和 [单元测试](https://github.com/langchain-ai/social-media-agent/actions/runs/38256407738) 成功。失败根因未查明，不能据此宣称生产可用或认定所有功能失效。

### 2. TrendRadar：信息发现与去重

[项目说明](https://github.com/sansan0/TrendRadar/blob/master/README.md) 展示热榜、RSS、关键词筛选、去重及排名时间线。可借鉴来源记录、去重和变化追踪，把外部信息整理成待研究的问题。

热榜与排名说明关注度线索，不直接证明真实需求、本人适合表达的主题或内容的因果效果。来源覆盖和可读取性仍需逐项验证。代码采用 [GPL-3.0](https://github.com/sansan0/TrendRadar/blob/master/LICENSE)，若将来复用或分发，须另核对许可要求。

### 3. Agent 小红书工作台：阶段产物与发布确认

[README](https://github.com/EthanYoQ/agent-xiaohongshu-workbench/blob/main/README.md) 将定位、研究、选题、文稿、完整预览和人工确认分阶段组织。可借鉴阶段产物、版本记录、预览与确认，以及结果不明时不标记成功。

README 明确故事线依赖手动标记，不读取评论，也不同步创作后台；不能把它当作已有的发布后指标学习闭环。其固定高互动筛选会偏向成功样本，本机制仍需普通比较样本与反例。仓库为 [MIT 许可](https://github.com/EthanYoQ/agent-xiaohongshu-workbench/blob/main/LICENSE)；部分 macOS 安装包标为未签名、未公证，本次不安装或绕过安全警告。

### 4. agency-agents-zh：清楚的工作交接

[小红书推广示例](https://github.com/jnMetaCode/agency-agents-zh/blob/main/examples/workflow-xiaohongshu-launch.md) 可借鉴研究、创作、审阅、分析之间的交接：每步交付什么、下步需要什么证据。

只借鉴流程结构。示例数字、固定标签数量、标题公式以及未附可靠依据的算法权重或效果基准，均不作为平台事实、目标承诺或已验证规律。示例数据不进入真实实验记录。

## 暂不作为初版依赖

- **xiaohongshu-mcp**：[README](https://github.com/xpzouying/xiaohongshu-mcp/blob/main/README.md) 同时列有搜索读取与发布、评论等写入能力，并注明服务默认关闭鉴权；[Cookie 存储代码](https://github.com/xpzouying/xiaohongshu-mcp/blob/main/cookies/cookies.go) 将会话数据写入本地 JSON 文件，未见该路径提供加密。读取需求不能自动扩展成写入授权。初版不安装；将来需要先审查凭据保存、网络暴露、读写隔离和具体授权。
- **MediaCrawler**：[许可证](https://github.com/NanmiCoder/MediaCrawler/blob/main/LICENSE) 为非商业学习使用许可证，商业使用另有限制。不能因为代码公开就视为可直接用于商业内容运营，本次不接入。
- **WeWeRSS**：[仓库](https://github.com/cooderl/wewe-rss) 在检索时已归档。维护和适配风险尚未解决，不将其作为稳定的公众号研究基础。

## 对本机制的具体调整

1. 先写自己的观察与思考，再借外部信息补问题和证据。
2. 每步保留可审阅产物；保存明确的修改理由，而非只留下最终稿。
3. 区分两种反馈：编辑反馈改善表达与准确性；平台结果反馈用于检验内容假设，两者分别记录。
4. 假设必须留下比较对象、反例、替代解释和未知项，不能将相关性写成确定因果。
5. 真正的反馈学习仍依赖已授权发布、可靠的同窗口数据和复盘；以上项目不能替代这一验证过程。

本次只补充方法与参考，不改变账号、权限、排程、登录或自动发布状态。
