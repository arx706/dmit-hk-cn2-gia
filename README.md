# 香港云服务器推荐：分清国际线路和 CN2 GIA 的区别，再按访问人群和预算挑套餐

搜"香港云服务器推荐"的人，最后大多栽在同一个地方：下单前只对比了配置和价格，买完才发现线路选错了。

香港机房免备案、离大陆近，这已经是共识，但共识不解决实际问题。同样是 1 核 1G，走国际 BGP 的和走 CN2 GIA 的，晚高峰能差出一个量级；同样的预算，月付和年付算下来的年度成本可能差 40% 以上。更麻烦的是，很多商家的产品页只写"香港 CN2"，不告诉你回程走哪条线。

所以这篇文章不打算给你一份"十大商家排行榜"。先把判断标准摊开，再用一个真实节点把标准落地——DMIT 的香港机房同时挂着国际线路、CMI 回程和 CN2 GIA 三种路由方案，档位从年付 36.9 美元到月付 759.9 美元，拿来当参照物刚好。

## 挑香港云服务器，真正决定体验的是三件事

### 一、线路，而不是 CPU 主频

延迟有三个来源：物理距离、去程线路、回程线路。物理距离你改不了，香港到华南单程十几毫秒是天花板。真正能上下浮动的是后两项。

香港机房常见的三种路由：

- **国际线路（Tier 1 / 国际 BGP）**：接入 RETN、NTT、Lumen 这类国际 Tier 1 运营商，香港连欧洲、东南亚很快，但对中国大陆没有专项优化。电信用户买这类套餐，延迟有可能比美西还高。
- **CMI 回程（移动优化）**：回程走中国移动国际线路，移动用户体感最好，电信联通通常要绕一段。价格一般处在中间档。
- **CN2 GIA（三网双向优化）**：电信去回程都走 CN2 GIA，联通走 AS4837 + AS10099，移动走 CMI，三家运营商都不偏科。代价是贵，通常是同配置国际线路的好几倍。

判断标准很简单：**你的访问者主要在哪，就买哪条线路**。这条定错了，加再多内存也救不回来。

### 二、免备案是事实，但"香港"不等于"晚高峰不卡"

香港机房普遍不需要 ICP 备案，这是它的核心优势之一。但同样是香港，不同机房的上游带宽、路由调度、超售比例差别很大。便宜的套餐往往共享带宽，白天测速很好看，晚上八点开始掉速。所以测试 IP 这个东西不是摆设——下单前自己 ping 一下，比看任何测评都准。

### 三、计费方式决定第二年的成本

这里有个很容易忽略的差别：流量用完之后会发生什么。

- 有的产品直接暂停账户，要等下一个计费周期才能继续用；
- 有的产品降速继续跑，不断线。

对建站和跑接口的业务来说，第二种更安全；对大流量下载、分发类业务来说，第一种反而意味着你得提前买够流量，否则高峰期断服。

另外年付通常比月付便宜不少，但前提是你确定这个节点会长期用。第一次买，先月付试一条，比一次性砸年付稳妥。

## DMIT 香港节点：把三种线路分开卖的少数商家

DMIT 是一家 2018 年开始做 VPS 业务的服务商，机房布局在洛杉矶、香港、东京三地，香港节点部署在 Equinix HK2，机房位置在葵涌，IP 归属 AS906 DMIT Cloud Services。它支持支付宝、PayPal 和信用卡付款，对国内用户来说付款环节没什么障碍。

把它放进推荐清单的原因是产品结构够清楚：香港同一机房下分 Premium（CN2 GIA）、Eyeball（CMI 回程）、Tier 1（国际线路）三条线，硬件平台都基于 KVM + AMD EPYC，你自己按访问人群对号入座就行，不用猜。

想自己先验一下延迟，可以用官方测试 IP：Premium 系列是 `103.117.100.199`，Eyeball 系列是 `154.12.188.3`。DMIT 还提供了公开的 Looking Glass 页面，可以直接从香港节点发起 ping 和路由追踪。这一步花两分钟，比看十篇测评有用。

## DMIT 香港全套餐价格对比

香港机房近期做过一次硬件代际切换：原来的 HKG.Pro 系列（AS3，AMD EPYC 7003）已经升级为 HKG.AN5.Pro（AMD EPYC 9005 + DDR5）。同一个档位名称在不同代际下配置和价格不完全一样，下面的表格以当前在售的 AN5 代际为主。

### Premium 系列（HKG.AN5.Pro）——三网 CN2 GIA

| 套餐 | CPU / 内存 / 硬盘 | 流量与带宽 | 价格 | 购买 |
| --- | --- | --- | --- | --- |
| TINY | 1 核 / 1GB / 20GB SSD | 500GB · 1Gbps | $39.9/月 | [以 $39.9 起查看 Premium 套餐](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| STARTER | 1 核 / 2GB / 40GB SSD | 1000GB · 1Gbps | $79.9/月 | [查看 Premium STARTER 档](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| MINI | 4 核 / 4GB / 80GB SSD | 1500GB · 1Gbps | $149.9/月 | [查看 Premium MINI 档](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| MICRO | 4 核 / 4GB / 160GB SSD | 2000GB · 1Gbps | $199.9/月 | [查看 Premium MICRO 档](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| MEDIUM | 6 核 / 8GB / 160GB SSD | 2500GB · 1Gbps | $279.9/月 | [查看 Premium MEDIUM 档](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| LARGE | 8 核 / 16GB / 320GB SSD | 3000GB · 1Gbps | $359.9/月 | [查看 Premium LARGE 档](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |
| GIANT | 12 核 / 24GB / 640GB SSD | 6000GB · 1Gbps | $759.9/月 | [查看 Premium GIANT 档](https://www.dmit.io/cart.php?region=hong-kong&generation=an5&network=premium&aff=12046) |

线路说明：电信去程 CN2 GIA 直连香港 CTG，回程同样走 CN2 GIA；联通走 AS4837 + AS10099；移动走香港 CMI 直连。默认自带 1 个 IPv4 和 1 个 /64 IPv6。流量用完后账户暂停，不会降速续跑。

Premium 目录下的低价档（TINY、STARTER）在第三方整理和官方购物车里出现过 `$119.9`、`$179.9` 一类的旧记录，这是 AS3 代际沿用下来的数据。下单前请以购物车实时显示为准——这类信息变动频率比大多数人想象的高。

### Eyeball 系列（HKG.EB）——CMI 回程，性价比档

Eyeball 分 AS3 和 AN5 两个硬件平台，价格差得比较明显：

| 平台 | 套餐 | CPU / 内存 / 硬盘 | 流量与带宽 | 价格 | 购买 |
| --- | --- | --- | --- | --- | --- |
| AS3 | EB.WEE | 1 核 / 1GB / 20GB SSD | 500GB · 500Mbps | $24.9/月 | [查看 Eyeball 入门档](https://www.dmit.io/aff.php?aff=12046) |
| AS3 | EB.TINY | 1 核 / 1GB / 20GB SSD | 800GB · 1Gbps | $39.9/月 | [查看 Eyeball TINY 档](https://www.dmit.io/aff.php?aff=12046) |
| AS3 | EB.STARTER | 1 核 / 2GB / 40GB SSD | 1.5TB · 1Gbps | $79.9/月 | [查看 Eyeball STARTER 档](https://www.dmit.io/aff.php?aff=12046) |
| AS3 | EB.MINI | 2 核 / 4GB / 60GB SSD | 2.2TB · 1Gbps | $126.9/月 | [查看 Eyeball MINI 档](https://www.dmit.io/aff.php?aff=12046) |
| AS3 | EB.MICRO | 4 核 / 4GB / 80GB SSD | 3TB · 1Gbps | $179.9/月 | [查看 Eyeball MICRO 档](https://www.dmit.io/aff.php?aff=12046) |
| AS3 | EB.MEDIUM | 4 核 / 8GB / 160GB SSD | 4TB · 1Gbps | $239.9/月 | [查看 Eyeball MEDIUM 档](https://www.dmit.io/aff.php?aff=12046) |
| AN5 | EB.TINY | 4 核 / 4GB / 80GB SSD | 2.2TB · 1Gbps | $149.9/月 | [查看 AN5 Eyeball TINY 档](https://www.dmit.io/aff.php?aff=12046) |
| AN5 | EB.STARTER | 4 核 / 4GB / 160GB SSD | 3TB · 1Gbps | $199.9/月 | [查看 AN5 Eyeball STARTER 档](https://www.dmit.io/aff.php?aff=12046) |
| AN5 | EB.MINI | 6 核 / 8GB / 160GB SSD | 4TB · 1Gbps | $279.9/月 | [查看 AN5 Eyeball MINI 档](https://www.dmit.io/aff.php?aff=12046) |
| AN5 | EB.MICRO | 8 核 / 16GB / 320GB SSD | 4.5TB · 1Gbps | $359.9/月 | [查看 AN5 Eyeball MICRO 档](https://www.dmit.io/aff.php?aff=12046) |
| AN5 | EB.MEDIUM | 12 核 / 24GB / 640GB SSD | 9TB · 1Gbps | $759.9/月 | [查看 AN5 Eyeball MEDIUM 档](https://www.dmit.io/aff.php?aff=12046) |

这里必须说一句实话：**DMIT 官方目前仍把香港 Eyeball 网络标注为 Beta**，产品和路由还在调整中，官方说明里也提到不建议用于对稳定性要求较高的生产环境。同价位下 Eyeball 的流量大约是 Premium 的 1.6 倍，回程走联通 CUG + CMI 动态负载、移动 CMI、电信 163，去程电信走 CN2、联通和移动没有专门优化。适合预算有限、访问者以移动网络为主、或者本身只是拿来做测试和轻量业务的人。

### Tier 1 系列（HKG.T1）——国际线路，大流量低单价

| 套餐 | CPU / 内存 / 硬盘 | 流量与带宽 | 价格 | 购买 |
| --- | --- | --- | --- | --- |
| WEE | 1 核 / 1GB / 20GB SSD | 1000GB · 4Gbps | $36.9/年 | [查看 Tier 1 年付入门档](https://www.dmit.io/aff.php?aff=12046) |
| TINY | 1 核 / 1GB / 20GB SSD | 2000GB · 4Gbps | $6.9/月 | [查看 Tier 1 TINY 档](https://www.dmit.io/aff.php?aff=12046) |
| STARTER | 1 核 / 2GB / 40GB SSD | 4000GB · 4Gbps | $12.9/月 | [查看 Tier 1 STARTER 档](https://www.dmit.io/aff.php?aff=12046) |
| MINI | 2 核 / 2GB / 60GB SSD | 8000GB · 4Gbps | $21.9/月 | [查看 Tier 1 MINI 档](https://www.dmit.io/aff.php?aff=12046) |
| MICRO | 4 核 / 4GB / 120GB SSD | 16TB · 4Gbps | $32.9/月 | [查看 Tier 1 MICRO 档](https://www.dmit.io/aff.php?aff=12046) |

Tier 1 最大的特点是**流量用完不断线**，超量后降速继续跑，不同档位限速从 50Mbps 到 1Gbps 不等。带宽给到 4Gbps 端口，价格却是三个系列里最低的。代价是完全没有大陆优化——如果你的用户主要在国内，尤其是电信和联通用户，这一档不适合你。

香港 T1 之上还有更高内存和流量的档位，以及一个已从 "Lite" 更名为 "Standard" 的香港大带宽产品线，具体配置和库存请直接在购物车里看。

## 按实际场景对号入座

**场景一：用户主要在大陆，延迟和稳定性不能将就。** 直接上 Premium（HKG.AN5.Pro）。TINY 档月付 39.9 美元只是个门槛价，配置不高；真正跑正经业务，MINI 起步更合适。这是三条线里唯一三网都不偏科的方案，价格也是最高的。

**场景二：移动用户占多数，预算减半。** 看 Eyeball。同样一个入门档，EB 的流量比 Pro 多，价格低一截。但先把 Beta 这个前提想清楚：能接受路由随时调整，再买。

**场景三：做跨境业务、面向海外用户，或者手里有自己的中转方案。** Tier 1 就是为这类需求准备的。年付 36.9 美元起步，4Gbps 端口，超量限速不断线。香港到欧洲的延迟在同类产品里属于比较低的一档。

**场景四：第一次用，不确定留不留。** 先月付买一台最低档，自己挂个测试页跑一周，看晚高峰延迟和丢包。这笔钱花得比任何攻略都值。

## 优惠码：能查到和查不到的都要说清楚

DMIT 的优惠码跟着库存和活动走，官方不会长期公示，第三方整理的时效性也参差不齐。目前能找到的、有明确适用范围的有这几个：

| 优惠码 | 适用范围 | 折扣 |
| --- | --- | --- |
| `202510_HKG_TYO_PRO_20OFF_RECURRING` | 香港 Pro / 东京 Pro，季付及以上 | 8 折，循环 |
| `202510_HKG_TYO_T1_30OFF_RECURRING` | 香港 T1 / 东京 T1，季付及以上（不含 WEE） | 7 折，循环 |
| `HKG-EB-V2-ANNUALLY-15OFF-RECUR` | Eyeball 年付 TINY 及以上 | 85 折，循环 |
| `Lite-Annually-Recur-30OFF` | Standard 网络系列，年付 | 7 折 |
| `Lite-Semi-Annually-Recur-20OFF` | Standard 网络系列，半年付 | 8 折 |

方法是在购物车里选好套餐和计费周期，把优惠码填进去点 "Validate Code"。能验证通过才说明当前有效，直接跳过这一步下单是不成立的。

另外也有整理的页面明确写着"当前暂无有效优惠码，已是特价"。这两种说法同时存在，正说明第三方整理的可靠性有限。所以上面这张表当作线索，不当作承诺。

想直接用钱说话，可以先去购物车看一眼实际价格：👉 [查看 DMIT 香港节点当前全部套餐与实时价格](https://www.dmit.io/aff.php?aff=12046)

## 付款、开通和几个容易踩的坑

付款方式支持支付宝、PayPal 和信用卡（含银联），这对国内用户是件省事的事。下单后一般能较快开通，具体以订单状态为准。

几个买之前值得确认的点：

- **库存是浮动的。** 香港 Pro 系列多次出现过缺货、补货的循环，看到合适的档位没了，不一定是永久下架。
- **超量规则不一样。** Premium 和 Eyeball 流量用完后暂停账户，Tier 1 降速继续跑。这两件事的后果完全不同，买之前想清楚你的业务能不能承受断服。
- **续费价格看计费周期。** 循环折扣类的优惠码续费同样生效，非循环的只管首次。年付通常比月付划算，但也意味着把决定权一次性交出去一整年。
- **IP 属性。** 香港节点的 IP 归属在 AS906。如果你对 IP 纯净度有特定要求（比如做流媒体或电商账号运营），这条得自己核一遍再下单。

## 常见问题

**香港云服务器需要备案吗？**
不需要 ICP 备案。这也是香港机房被大量跨境业务选中的直接原因之一。

**为什么同样是香港，延迟能差出这么多？**
物理距离决定了延迟的底线，回程线路决定了你能不能守住这条底线。国际线路回大陆经常绕行，CN2 GIA 走专用链路，两者在晚高峰的差别最明显。

**DMIT 香港三条线，新手选哪条最不容易出错？**
如果访问者主要在国内、又不想反复折腾，Premium 是唯一不需要赌的选项，代价是价格最高。想省钱又愿意承担一定波动，选 Eyeball。纯粹面向海外，选 Tier 1。

**年付的 36.9 美元是全价吗？**
那是 Tier 1 的 WEE 档年付价格，属于香港节点里最低的门槛。它没有任何大陆线路优化，别看到数字低就直接下单。

## 最后

香港云服务器推荐这个问题的答案，取决于你的访问者在哪里，而不取决于哪个商家广告打得响。

把线路搞清楚，把超量规则搞清楚，把第二年的续费价格算清楚——这三件事做完，剩下的就是预算问题了。DMIT 的价值在于它把三种线路摆在同一个机房里明码标价，你可以按需求挑，而不是被一个笼统的"香港 CN2"糊弄过去。

想自己验证延迟再决定，先拿测试 IP ping 一轮；想直接比价，就进购物车把三条线的价格并排看一遍：👉 [查看 DMIT 香港 Premium / Eyeball / Tier 1 全部套餐](https://www.dmit.io/cart.php?region=hong-kong&aff=12046)
