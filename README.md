# 亚马逊选品方法手册：从机会发现到验证

[下载 PDF 版](docs/amazon-sourcing-playbook-2026-11-16.pdf)

适用：以 Amazon 美国站为主，兼顾其他跨境平台。公开资料核查日期：2026-11-16（北京时间）。本手册不推荐具体商品，不改项目筛选标准。

**把选品分成三个不同的问题：买家有什么事没解决？有没有证据表明他会在亚马逊买？我们能否在目标价格下解决它并赚钱？** 第一个问题可以从社区、评论、众筹和其他平台发掘；第二个要回 Amazon US；第三个要靠实物、报价和测试。单一榜单、搜索量、评论数或 AI 分数回答不了这三个问题。

## 可安装的选品 Skill

[查看 Skill](skills/amazon-product-discovery/SKILL.md) · [方法执行卡](skills/amazon-product-discovery/references/methods.md) · [机会卡模板](skills/amazon-product-discovery/assets/opportunity-card.md)

技能名称：`amazon-product-discovery`。支持选品方法研究、场景机会扫描、候选复核以及评论、众筹等单项研究。它把下方手册的 11 种方法转成按任务选用的操作流程，优先使用公开资料，结论带来源、日期、口径和反证。

### 安装与调用

使用支持 GitHub 目录的 Skill 安装器，指定本仓库及目录 `skills/amazon-product-discovery`，安装整个文件夹，包括 `references/`、`assets/` 和 `agents/`。只复制入口文件会缺少方法与模板。仓库上传与本机安装是两个步骤。

在有 Skill 安装器的 Codex 中，可以发送：

> 请从 https://github.com/TomorrowLee/Amazon-Product-Selection 安装 skills/amazon-product-discovery 目录中的 Skill。

安装并在当前工具中可用后，可按任务调用：

```text
使用 $amazon-product-discovery，研究适合亚马逊美国站的选品方法，
从公开社区、官方资料、GitHub 和众筹网站寻找做法，比较适用条件，
输出方法、来源和验证流程。
```

```text
使用 $amazon-product-discovery，从美国用户的使用困难出发，
研究我指定场景的需求机会，回 Amazon 验证供给，
输出机会卡、改进假设、反证和最低成本验证动作。
```

```text
使用 $amazon-product-discovery，按当前项目已经确认的标准复核候选，
分别列出已证实不符与未获取字段，并附来源和日期。
```

Skill 会读取所在项目的规则及可用的标准文件。下方手册中的销量、上架、Review、变体数字是原项目配置，安装到其他项目时不会自动作为通用门槛。无账号数据权限时，以公开资料开展研究并保留缺口；采购、联系供应商、广告投放和最终决策不因调用本 Skill 自动获准。

---

## 一、11 种方法：每种该什么时候用

| 方法 | 如何执行 | 如何判断走错了 |
| --- | --- | --- |
| **1. 从「凑合做法」找需求** | 在目标市场的 Reddit、垂直论坛、零售商问答里找用户具体做过的事：自己改装、临时固定、买两个东西配合、替换零件、反复退换。记录「谁—什么任务—卡在哪一步—怎么凑合—付出了什么」。小红书适合用中文场景词拓宽视野，再到美国用户原帖核验。参考：[知无不言：需求先行](https://www.wearesellers.com/question/123662)、[单干卖家的站外搜寻经验](https://www.wearesellers.com/question/90898)、[小红书搜索工具](https://ad.xiaohongshu.com/next_help/docs/d6e54d83d20628f893180ec49b790cbd)。 | 只有泛泛的「不好用」、点赞，或同一篇教程被大量转载；没有观察到可重复的真实行为。不能用中文社区热度推断美国需求。 |
| **2. 用购买意图词反查** | 把线索译成美国买家用的三类词：任务/场景、用途/现有解法、适配限制/功能。固定 US 配送地和查询时间，从亚马逊联想及搜索结果中查看同一任务有哪些不同解法，标记广告、无关品和同家族重复项。不要按字面把「做相同任务」误当「搜同一个品名」。参考：[Amazon 卖家论坛：如何定义细分市场](https://sellercentral.amazon.com/seller-forums/discussions/t/681c4de8-ceaa-4042-b41f-dedd05662535)。 | 核心词搜出来基本是别的用途、品牌指名流量，或精确意图只在一个很窄的词上有迹象。不能把大词总量计入细分需求。 |
| **3. 找有搜索但供给没跟上的细分** | 有权限时，在 Product Opportunity Explorer 对照搜索趋势、搜索后购买表现、点击集中、价格和现有方案，再查是否缺特定功能、规格或价位。用 Brand Analytics 的 Top Search Terms 查头部集中，已有品牌可以用 Search Query Performance 查与自己品牌/ASIN 相关的曝光、点击、加购、购买。仅用公开资料时做同意图商品盘点，无法观测的转化和份额记「未获取」。参考：[POE 原始说明](https://sellingpartners.aboutamazon.com/product-opportunity-explorer)、[Brand Analytics](https://sell.amazon.com/tools/amazon-brand-analytics)。 | 搜得多、买得少也可能源于意图混杂、商品断货、说明不清或价格高。要用真实用户反馈和供给对照排除其他解释；不能直接宣布「蓝海」。 |
| **4. 看同批新进入者，验证新人能否做起来** | 固定一个购买意图，分开老链接和可核验的新上架链接。对照后者的历史排名、价格、促销、可见近月购买标签，以及是否来自多个独立品牌。保留没有起量的可见新品作为对照。核对父体、子体和最早留档，不把老家族加款当独立新品。参考：[Amazon 卖家论坛：BSR 与关键词排名](https://sellercentral.amazon.com/seller-forums/discussions/t/5cd0156f-ecdd-48fa-86fe-6b6612b383f4)、[GitHub：新品突破策略卡](https://github.com/liangdabiao/amazon-sorftime-research-MCP-skill/blob/main/SKILLS/skills/sellersprite-amazon-research/README.md)。 | 只有一个强品牌、一波大折扣或一个迈进榜单的幸存者。看得到的新品不是新品总数；不计算全市场「上新成功率」，不用通用 BSR 对照表填实际销量。 |
| **5. 从跨竞品评论找可改的缺陷** | 对同使用场景的多个独立品牌抽查近期低星和高星评论、问答；按具体规格、时间与原因去重，区分产品故障、页面预期、运输破损及偏好。记录抽样分母、跨竞品覆盖、原文和反例，把问题改写成一个可检验的规格或样品验收动作。参考：[亚马逊全球开店选品问答](https://globalselling.amazon.com/learn/faq)、[Amazon 变体评论共享公告](https://sellercentral.amazon.com/seller-forums/discussions/t/a572986d-9bb1-4e91-a53f-41c575874dd7)。 | 问题只出现在单一供应商或旧规格，已经被新款解决，或根因无法通过改款改变。只抽低星不能估全体投诉率或退货率。 |
| **6. 反查品牌、本土零售和相邻任务** | 找目标市场的独立品牌、专业零售商、Amazon 店铺；看它们在一个用户群上连续扩了什么，沿「使用前—使用中—使用后」找替换、适配、补充、组合。对每个相邻方向重新回 Amazon 查价格、搜索结果和需求。参考：[知无不言：本土店跟踪和五类差异化](https://www.wearesellers.com/question/120198)。 | 门店上新、品牌关注或购物推荐本身没有证明销量，也不证明适合独立做套装。组合只有减少漏买、安装失败或购买决策成本，才有可验证的理由。 |
| **7. 看历史，拆开常青、季节和促销峰值** | 用 [Google Trends](https://support.google.com/trends/answer/4365533?hl=en) 固定美国与同一词组对比多年同期，再看 Amazon 历史价格和同类目 BSR；检查峰值是否与促销、天气、节日或缺货重合。可用 [Keepa](https://keepa.com/) 的历史图辅助；看引发峰值的条件，倒推开发、生产、入仓能否赶上。 | Google Trends 是相对搜索兴趣；不同查询分别跑出的 100 不能直接比绝对体量。BSR 是类目名次。仅有短期跳升先观察，不外推年需求。 |
| **8. 众筹看付费意愿和交付难点** | 在 [Kickstarter 产品设计](https://www.kickstarter.com/discover/categories/design/product%20design) 和 [Indiegogo](https://www.indiegogo.com/en/projects/search) 找同一问题的多个项目，尽量包含未达标、延期和已交付。比较支持者人数、相近档位实际权益和一件到手成本、更新与评论；看有无普通零售对照。参考：[Kickstarter 支持机制](https://updates.kickstarter.com/how-to-back-a-crowdfunding-project-on-kickstarter/)、[募足后仍可能交付失败](https://updates.kickstarter.com/why-kickstarter-campaigns-fail-after-funding-and-how-to-avoid-it/)。 | 早鸟、套装、品牌粉丝与媒体曝光会影响支持表现。支持金额不能换算成零售销量；未达标项目里的承诺不等于实际付款。项目页可借来研究场景、定价和缺点，不复制设计。 |
| **9. 带着供应链能力反向选市场** | 从已有可稳定控制的材料、工序、包装尺寸、最小订量和交期出发，找能复用的用户需求与现有解法；把同一规格做成可比较的报价表，列模具、包装后尺寸、抽检和补货周期。再回 Amazon 验证市场。参考：[知无不言：选品与供应链](https://www.wearesellers.com/question/90898)、[亚马逊全球开店选品问答](https://globalselling.amazon.com/learn/faq)。 | 厂家「爆款」或 1688 报价缺同规格、数量、包装和到岸口径。便宜不等于有需求，公模也不能证明有销售权或合规。 |
| **10. 先算保本，再看销量与售价** | 用包装后尺寸/重量和合理成交价跑 [Amazon 收入计算器](https://sell.amazon.com/pricing/estimate)，再补到岸、入仓、仓储、促销、退货损失和获客成本。对成交价下降、退货上升、费用升级分别算，再看叠加。参考：[雨果跨境：高销量不代表赚钱的复盘](https://www.cifnews.com/article/188725)。 | 只能按标价赚钱、忽略退货，或有广告就亏且没有证据能改善。估算费用跟实测报价分列，不能拿卖家自报毛利当行业阈值。 |
| **11. 用最便宜的实验否掉假设** | 先做场景访谈、原型对照或样品试用；通过后，再考虑人工批准的小批量测试。预先写下目标价格、预算、看哪些结果和何时停。区别曝光不足、被看到但不点、点了但不买、买后集中退货；一次只改一类因素。参考：[AMZ123：新品试跑与停损](https://www.amz123.com/t/GBZHeQ05)、[Amazon 内容 A/B 工具和资格](https://sell.amazon.com/tools/manage-your-experiments)。 | 低价促销能出单，恢复目标售价就不买；或者原型问题无法解决。内容 A/B 能检验商品页面表达，不代替新市场需求或产品质量测试。 |

## 二、什么时候该用哪个数据

| 信号 | 能说明什么 | 不该拿来说明什么 |
| --- | --- | --- |
| Amazon US 商品页、榜单和公开搜索页 | 某日某站点的公开报价、规格、页面可见变体、购买档位、类目排名和可见货架结构。 | 真实单 ASIN 月售件数、精准广告占比或类目份额。Amazon 把购买标签称为近月客户购买的大致估计；缺标签不等于零销量。[Seller Forums 公告](https://sellercentral.amazon.com/seller-forums/discussions/t/732ded0cef8e8ee8c2a7caf832bc85f0) |
| POE、Brand Analytics | 有权限时验证 Amazon 上的实际搜索和购买行为，但要按仪表盘说明区分细分、词、品牌和 ASIN 的范围。 | 不把细分数据分摊成竞品销量；不把与自己品牌相关的搜索漏斗当全市场。[POE](https://sell.amazon.com/tools/product-opportunity-explorer) · [Brand Analytics](https://sell.amazon.com/tools/amazon-brand-analytics) |
| 评论、问答、站外使用讨论 | 任务、适配、故障和现有替代办法；有助于写样品测试。 | 不能把评价数增长换算销量；同一买家、帖子转载、同变体家族不算多个独立事实。评分总数、文字 Review 和你抽到的样本数分列。 |
| 早期公开留档、历史排名、第三方销量工具 | 各自可用来辨识是否早已出现、趋势、交易强弱估计。 | 最早抓取/评论证明「最迟当时已经存在」，不证明首次上架；多个基于相似排名输入的估算不构成独立验证。 |

最低记录格式：**主张｜原值｜来源链接｜检索日期｜站点｜时间窗口｜商品或父子体层级｜口径（平台原值 / 第三方估计 / 用户描述 / 待检验假设）｜反证**。来源独立性按原始事实算，不按域名算。知无不言的需求帖与 AMZ123 文章可用于比较步骤；方法相近不算独立验证。AMZ123 所引文章由站外促销服务商发布，参考其试验设计，不把促销表现当常价需求。小红书搜索工具官方说明可核查，部分公开笔记正文未稳定获取，因此不引用无法回看的笔记，也不采用其成交数字。

## 三、接入现有 Amazon US 漏斗

1. **先建机会池。** 同时走三条线：站内关键词/POE，站外使用困难/众筹，供应链/本土店。每条线留「需求句、原始证据、英文检索词、能推翻它的条件」。还没有可比 ASIN 的新概念留在灵感池，不能靠同类总量代填某个商品的销量。
2. **建至少 20 个 ASIN 组成的初筛池。** 从与目标任务匹配的真实商品入池，记录站点与实际规格，查历史去重。按已确认标准查 US、类目、月销量至少 100、上架不超过 6 个月、Review 至多 200、变体至多 3。每条区分「已证实不符」和「未获取」。公开购买档位放独立列；如果只有档位或估计，保留证据缺口。
3. **10 个做深查。** 尽量覆盖不同结构，包含直竞、替代方案和新进入者。每个对象对照五件事：需求有没有重复证据、前排为什么卖、至少一个可验证的改进、目标价格下能不能覆盖成本、哪条反证会推翻它。同类样本集中度必须写分母；收集不到 POE 或后台数据就不报店铺或品牌份额。
4. **最多 5 个进入人工审核短名单。** 硬门槛明确不符的退出；关键证据缺失的另列补证，不为凑数升档。有明确需求、可交付差异、成本和风险有核验路径的对象才进入审核。人工确认知识产权、合规、供应链、成本以及最终决策；知识产权与安全验证的入口有 [USPTO 专利检索](https://www.uspto.gov/patents/search/patent-public-search) 和 [CPSC 企业指引](https://www.cpsc.gov/Business--Manufacturing/Business-Education)。

深查时可用一条简单算式倒推：**广告前单件贡献 = 净成交收入 − 到岸货值及物流 − 佣金和配送等费用 − 仓储与预期退货损失**。促销折扣与退货退款在所用口径各扣一次。若用付费点击测试，且用同一时间窗口、相同归因，**保本 CPC ≈ 每次点击带来的订单率 × 广告前每单贡献**。它是试算，不是项目新增门槛；实际订单多件、退货及归因延迟要按实测修正。

## 四、其他跨境平台怎么补位

| 平台 | 去看什么 | 如何回到 Amazon |
| --- | --- | --- |
| [eBay Product Research](https://www.ebay.com/help/selling/selling-tools/product-research?id=4853) | 以成交价格和成交趋势对新旧成色、配件、维修替换件等做对照；统一站点和含运费口径。 | 优先验证适配问题和规格。eBay 成交不当 Amazon 销量，二手价格不当新品价格。 |
| [Etsy Marketplace Insights](https://help.etsy.com/hc/en-us/articles/35122361353239-How-Do-I-Use-Etsy-s-Marketplace-Insights-Tool) | 用 Etsy 搜索与在售商品数发现个性化、礼品用途、材质、风格和人群词。 | 搜索多不能直接证明销量；只带走使用场景、表达方式和意图词，核对 Amazon 对应供给。 |
| [TikTok Top Ads](https://ads.tiktok.com/resources/help/article/how-to-use-the-top-ads-dashboard) / [TikTok Shop Product Insights](https://seller-us.tiktok.com/university/essay?knowledge_id=7067468817090317) | Creative Center 的广告榜观察能够快速展示的功能与问题；具备相应权限时，另读 Product Insights 的订单指标。 | 分开「能拍出效果、能引点击」和「用户会主动搜索并在目标价购买」。检查亚马逊的搜索证据、常价和退货。 |
| [小红书聚光搜索工具](https://ad.xiaohongshu.com/next_help/docs/d6e54d83d20628f893180ec49b790cbd) | 站内找场景原话、使用限制、对比或避雷反馈。有权限时用词与笔记信号拓展问题，而不是把营销文案计为买家反馈。 | 把场景译成英文问题句，用美国论坛、零售问答和 Amazon US 搜索独立验证。 |

## 五、GitHub 和 AI 怎样落到日常

- **把选品动作写成短流程。** [Amazon Research 策略卡库](https://github.com/liangdabiao/amazon-sorftime-research-MCP-skill/blob/main/SKILLS/skills/sellersprite-amazon-research/README.md) 可参考「新品突破、关键词集中度、口碑缺口」的拆法；[PDBen 的研究工作流](https://github.com/PDBen-Auto/amazon-product-research-agent-skills) 可参考如何把评论、差异化、供应链和决策分开。它们是第三方工作流和工具，不是独立销量数据；不照搬里头的行业阈值。本次未安装或调用这些项目。
- **把证据做成可以重跑的分析。** [BERTopic](https://github.com/MaartenGr/BERTopic) 可用来对有权使用的评论做主题归类；[Amazon Reviews 2023 研究数据](https://amazon-reviews-2023.github.io/) 适合试分类和检验去重，不能当作当前评论或销量。需要历史字段的复用方案可看 [Keepa Python 客户端](https://github.com/akaszynski/keepa)，开源客户端和需授权的数据服务是两回事。
- **给 AI 一项能验收的工作。** 让它把已给出的原话按「任务、限制、凑合法、目前解法」归组，给出英文任务词、形态词和适配词；每条都回链，标记是否为同一买家或转载。再让它为每个机会写一条反证和一个最低成本测试。真实数字靠原页面或已授权数据核验，缺失写「未获取」。

开搜时先用「场景＋怎么处理／替代／翻车」找行为，再用 `"how do you" + [任务]`、`"workaround" + [限制]` 找美国用户原话；回 Amazon 把「用途＋关键适配条件」作为购买词查供给。若只搜已有商品的名称，容易漏掉用另一种形态完成同一任务的替代品。

可复制的一张机会卡：

> **需求句**：谁，在什么场景，要完成什么任务，受什么限制？  
> **行为证据**：买家怎样凑合？有哪些独立原文？  
> **站内核验**：哪些英文词和 ASIN 相关？现有解法、价格和需求证据是什么？  
> **我们的改法**：消掉哪个实际麻烦？样品怎么验收？  
> **反证和处置**：什么观察会让我们停止？继续补证、试样，还是排除？  
> **来源记录**：链接、日期、站点、层级、指标口径和缺失字段。

