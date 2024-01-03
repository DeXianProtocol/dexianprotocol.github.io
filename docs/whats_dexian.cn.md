---
layout: page
menubar: docs_menu
title: Disclaimer
show_sidebar: false
toc: false
---
DeXian Protocol是什么？
===========

## What's DeXian Protocol?
DeXian协议是基于Radix分布式帐本的流动性协议。通常流动性被理解为swap池中token供应，但是DeXian协议的流动性是更广泛的对特定数字资产(token)的需求和供给，基于去中心化，非托管原则，用Scrypto实现的满足流动性提供和流动性消耗者需求的一系列智能合约基础接口定义，功能实现封装。它就是DeXian协议的全部。

目前DeXian协议包括：

* Lending Protocol, 它是Radix分布式帐本上对某些数字资产的借贷协议，它可以为流动性提供者赚取更多Token，也可以为需要流动性消耗者及时、高效地提供token以便他们把握市场波动带来的机会。这是它的基本功能，由此还可以延便更多服务，包括闪电贷等等。
#### 闪电贷
是DeFi领域一种常见的即用即还借贷服务，因为DeFi服务类似于乐高积木，不同的协议，产品天然具备可组性，如果在同一个Transaction中获得借款后进行其它协议、产品的交换或使用，随后归还借款和费用的这种业务模型被称为闪电贷(Flash Loan).

* Staking Earing(DSE)，它是Radix网络上基原生Liquid Stake提供的组合便捷服务，总体来说：
#### 保障Radix保持更平衡健壮的网络基础设施
DSE通过公开的Staking Network数据结合平衡算法，在保障用户尽可能最大化Stake收益的前提下，均匀平衡地将XRD分布到不同验证器(validator)上，保障了Radix网络更加平衡，更加健壮和去中心化。
![staking rebalance](/assets/images/stake.png)
#### 可选的立即赎回(instant unstake)
DSE的持有者在赎回之前参与(join)的份额时，支持可选的快速赎回(Redeem)，能够以高效，低摩擦的方式快速获得流动性，而不必等到Unstake的周期到期，所需费用在立即赎回时一次性支付，费用的多少依据XRD流动性池的利率机制动态变化。
![redeem](/assets/images/unstake.png)
#### 广泛支持所有验证节点的赎回，认领操作。
不仅DSE的持有者可以便捷使用立即赎回功能，所有验证节点发行的LSUs都可以利用DeXian协议获得可选的立即赎回的能力，也可认领unstake后获得的ClaimNFT.
#### 为DSE提供XRD的流动性
所有XRD的持有者都可以为DSE池提供流动性，并分享流动性消耗者(立即赎回用记)支付费用收益。
![DeXian Liquidity Pool](/assets/images/dse_liquidity_pool.png)
#### 立即赎回的费用如何确定
因为目前unstake有一个星期的锁定期，立即赎回者需要支付一定费用，实际费用依赖XRD流动性的占用/空闲比例动态调整，在每次立即赎回时一次性扣除。目前以年化利率计算约为: 8%左右，按此数据一次赎回的费率约为：0.16%左右，即快速赎回10000XRD的费用为16XRD.

