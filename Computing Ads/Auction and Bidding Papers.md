# Auction & Bidding Papers

## Overview


generalized second price auction 第二价位竞拍
    - 在基于第二价位竞拍的形式下，广告商按照自己对于广告位价值的理解来竞拍是相对较优的策略。
    - Jun Wang, Weinan Zhang and Shuai Yuan. Display Advertising with Real-Time Bidding (RTB) and Behavioural Targeting. Foundations and Trends® in Information Retrieval: Vol. 11: No. 4-5, pp 297-435, 2017.
Bidding Landscape predictions - 对于“竞价全景观”或者是赢的价格分布的估计有一个比较困难的地方，那就是，作为广告商来说，往往并不知道所有其他竞争对手的出价，以及在没有赢得竞拍的情况下，那些赢得竞拍的出价是多少。简而言之，也就是我们只观测到了一部分数据，那就是我们赢得这些广告位的出价。在这种只有一部分信息的情况下，所做的估计就会不
    - Wu, W. C.-H., Yeh, M.-Y., and Chen, M.-S. Predicting winning price in real time bidding with censored data. Proceedings of the 21st ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 1305–1314. ACM, 2015.
    - 有学者认为，赢的价格服从一个“对数正态分布”（Log-normal）。也就是说，广告商出的价格并且最终赢得竞拍的这些价格，在取了对数的情况下，服从一个正态分布。
    - 利用了一种对数几率回归来估计那些没有赢得竞拍情况下的赢的价格，然后和已知的赢的价格一起对整个“竞价全景观”进行估计，这也算是目前的一项前沿研究。

## Auction (Machanism Design)

- 拍卖机制-诺贝尔奖论文
  - Jun Wang, Weinan Zhang and Shuai Yuan. Display Advertising with Real-Time Bidding (RTB) and Behavioural Targeting. Foundations and Trends® in Information Retrieval: Vol. 11: No. 4-5, pp 297-435, 2017.
- 竞价Bidding
  - Wu, W. C.-H., Yeh, M.-Y., and Chen, M.-S. Predicting winning price in real time bidding with censored data. Proceedings of the 21st ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 1305–1314. ACM, 2015.
- Optimal Bidding
  - Ramakrishna Gummadi, Peter Key and Alexandre Proutiere. Repeated auctions under budget constraints: Optimal bidding strategies and equilibria. In Eighth Workshop on Ad Auctions, 2012.
  - Yuan, S., Wang, J., and Zhao, X. Real-time bidding for online advertising: measurement and analysis. Proceedings of the Seventh International Workshop on Data Mining for Online Advertising, page 3. ACM, 2013. 
  - Andrei Broder, Evgeniy Gabrilovich, Vanja Josifovski, George Mavromatis, and Alex Smola. Bid generation for advanced match in sponsored search. Proceedings of the fourth ACM international conference on Web search and data mining (WSDM '11). ACM, New York, NY, USA, 515-524, 2011.
- bidding optimization
  - [1]Perlich, C., Dalessandro, B., Hook, R., Stitelman, O., Raeder, T., and Provost, F. Bid Optimizing And Inventory Scoring in Targeted Online Advertising. Proceedings of the 18th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 804–812. ACM, 2012.2. 
    - 线性出价策略在实际操作中比较方便灵活，在这篇论文中，这种算法也取得了比较好的效果。不过遗憾的是，这种做法并没有太多的理论支持。
  - Zhang, W., Yuan, S., and Wang, J. Optimal Real-Time Bidding for Display Advertising. Proceedings of the 20th ACM SIGKDD international conference on Knowledge discovery and data mining, pages 1077–1086. ACM, 2014.3. 
  - Zhang, W., Ren, K., and Wang, J. Optimal Real-time Bidding Frameworks Discussion. arXiv preprint arXiv:1602.01007, 2016.4. 
  - Zhang, W. and Wang, J. Statistical Arbitrage Mining for Display Advertising. Proceedings of the 21th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 1465–1474. ACM, 2015.
- pacing， budget pacing
  - 1. Lee, K.-C., Jalali, A., and Dasdan, A. Real Time Bid Optimization with Smooth Budget Delivery in Online Advertising. Proceedings of the Seventh International Workshop on Data Mining for Online Advertising, page 1. ACM, 2013.2. 
  - Xu, J., Lee, K.-c., Li, W., Qi, H., and Lu, Q. Smart Pacing for Effective Online Ad Campaign Optimization. Proceedings of the 21st ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 2217–2226. ACM, 2015.3. Agarwal, D., Ghosh, S., Wei, K., and You, S. Budget Pacing for Targeted Online Advertisements at Linkedin. 
  - Proceedings of the 20th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 1613–1619. ACM, 2014.4. 
  - Chen, Y., Berkhin, P., Anderson, B., and Devanur, N. R. Real-time Bidding Algorithms for Performance-based Display Ad Allocation. Proceedings of the 17th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, pages 1307–1315. ACM, 2011.5. Zhang, W., Rong, Y., Wang, J.,

## bidding strategies
    - 竞价的一个重要特征，就是作为一个竞标方，我们并不知道其他竞标方的点击率和出价。因此，我们处在一个信息不完整的竞价环境中。在这样的环境中，我们只能根据自己的点击率估计和自己的出价，以及过去出价的成功与否来对整个市场的形势进行判断。这就是在 RTB 中竞价策略的一大挑战和难点。
    - 思路是把整个竞价策略当做一种“博弈”（Game），从而根据博弈论中的方法来对竞价环境中各个竞标方的行为和收益进行研究（比较经典的论文例如参考文献[1]）。用博弈论的方法来对竞价进行研究有一个最大的特点，那就是博弈论主要是对各个竞标方行为之间的关联性进行建模，这种关联性包括他们之间的收益和他们的动机。
      - 也就是利用博弈论的方法来对竞价策略进行研究主要存在于学术界。虽然从理论上来说，博弈论可能提供一种比较有说服力的解释，但是这种思路需要对整个竞价环境有非常多的假设（例如竞标方是不是理性，市场是不是充分竞争等等）
    - 另外一种思路是把整个竞价策略当做是纯粹的统计决策，也就是直接对广告商的行为进行建模，而把整个竞价环境中的种种联系都当做是当前决策下的不确定因素（这种思路比较有代表性的论文是参考文献[2]）。在这样的思路下，各个竞标方之间的行为关联变得不那么重要，而对于整个不确定性的建模则变得至关重要。
      - 而第二种思路，仅仅需要从广告商自身的角度出发，因此在现实中，这种思路的操作性更强，从而受到工业界的青睐。
      - 第二种思路其实就是根据当前的输入信息，例如页面信息、广告信息、用户信息以及上下文信息等，学到一个输出价格的函数，也就是说，这个函数的输出就是在现在情况下当前广告的出价。当然，这个函数势必需要考虑各种不确定的因素。
    - 搜索vs展示
      - 对于搜索广告来讲，在大多数情况下，每一个出价都是针对某一个搜索关键词的
      - 参考文献[3]是第一个利用机器学习方法对搜索广告的出价进行建模的工作。在这个工作里，每一个关键词的出价来自于一个线性函数的输出，而这个线性函数是把用户信息、关键词以及其他的页面信息当做特性，学习了一个从特性到出价的线性关系。
      - 展示广告的竞价则面临着不同的挑战。首先，在展示广告中，场景中并不存在搜索关键词这种概念。因此，很多广告商无法针对场景事先产生出价。这也就要求 RTB 的提供商要能够在不同的场景中帮助广告商进行出价。
      - 相比于搜索广告针对每一个关键词的出价方式来说，针对每一个页面显示机会出价的挑战则更大。理论上讲，每一个页面显示机会的价格都可能有很大的不同。很多 RTB 都利用一种叫作 CPM 的收费模式，也就是说，一旦某一个广告位被赢得之后，对于广告商来说，这往往就意味着需要被收取费用。所以，在展示广告的情况下，如何针对当前的页面显示机会以及目前的预算剩余等等因素进行统一建模，就成为一个必不可少的步骤。
    - Pacing
      - 一个广告商现在有 1 千元的预算参与到 RTB 竞价中。从广告商的角度来说，通常希望这 1 千元能够比较均匀地使用到整个广告竞价中。或者说，即便不是完全均匀使用，至少也不希望这笔预算被很快用完。这里面的一个原因是，在每天的各个时段，广告的表现情况，也就是说转化率或点击率是不一样的，广告商通常希望自己的广告能够在比较好的时段进行展示
      - 告竞价策略中，还存在着一个叫“预算步调”（Budget Pacing）的技术，也就是希望能够让广告的展示相对平缓而不至于在短时间内使用完全部的预算。这势必对于广告如何出价有着直接的影响。
    - 对于平台而言，虽然竞价保证了一定的竞争，但是也并不是所有的展示机会都有非常充分的竞争。因此，从平台的角度来说，如何能够保证一定的收益就变得十分重要。在这样的情况下，有的平台有一种叫作“保留价格”（Reserved Price）的做法，用来设置一个最低的竞价价格。保留价格虽然能够来保证收益，但是也可能会让广告商觉得不划算，因此如何来设置这个保留价格，也就成为了出价策略中的一个重要组成部分。
    - optimal bidding
    - campaign level bidding optimization
      - 这里我们采用一个简化的假设，认为一个推广计划的出价是点击率的一个函数。
        - 第一个概念是“赢的概率”（Winning Probability）。这里面，如果我们知道现在市场的一个价格分布以及我们的出价。那么，赢的概率就是一个已知概率密度函数求概率的计算，也就是通常情况下的一个积分计算。
        - 第二个概念就是“效用”（Utility）。这是一个广告商关注的指标，通常情况下是点击率的某种函数，比如利润，那就是每一次点击后的价值减去成本。
          - 成本其实主要就是出价后产生的交易价格。如果是基于第一价位的竞价，那么这个成本就是出价；如果是基于第二价位的竞价，这个成本就是超过第二价位多少还能赢得竞价的价格。
        - 所有的广告推广计划都必须要在预算内，这是一个很明显的限制条件。
      - 假设，我们竞价的核心是所谓的“按照价值”的竞价。那么，在这种情况下，最优的策略其实就是按照点击率乘以点击后产生的价值来进行出价。可以说，这种策略其实是业界接纳程度最好、也是最直观的一种竞价策略。
      - 了预算和当前的交易流量信息的情况下，这种竞价策略就并不是最优的策略了。为什么呢？因为在有了这些限制条件的情况下，我们是否还会按照自己客观认为的广告价值来竞标就成了一个疑问。
        - 线性出价[1]与其完全按照广告的价值来进行出价，不如采用这个价值乘以某个系数，而利用这个系数来动态调整目前的出价。由于是在一个已知的可能出价前面乘以一个系数，所以整个出价策略其实是一种线性变换，因此也被叫作是线性出价策略。
          - 在这篇论文中，这种算法也取得了比较好的效果。不过遗憾的是，这种做法并没有太多的理论支持。
        - 【2】【3】这个框架的整体思路是把寻找最优出价，或者说是竞价函数的过程表达成为一个“有限制的最优化问题”（Constrained Optimization）。
          - 最优化的优化目标，自然就是当前竞价流量下的收益。而最优化的限制条件，就是竞价流量下的成本要等于预算。也就是说，在我们期望达到预算的情况下，我们需要尽可能地扩大收益，这就是最优化目标的最大化这个意思。而限制条件决定了这个最大化问题的解的空间，因此，那些不符合条件的解就可以不考虑了。
          - 一旦我们的问题可以用有限制的最优化问题来表达以后，整个问题的求解就变得相对比较规范化了。对于这类问题有一个标准的求解过程，就是利用“拉格朗日乘数法”，把“有限制的优化问题”转换成为“无限制的优化问题”，然后针对最后的目标函数，求导并置零从而推导出最优解的结果。这一部分的步骤是标准的高等数学微积分的内容。
          - 这个框架最后推导出了基于第一价位和基于第二价位的最优的出价函数形式。在两种情况下，最优的出价函数都是一个基于点击率、当前竞价流量和预算的非线性函数。那么，从这个框架来看，刚才我们提到的线性竞价策略就并不是最优的。
    - 多个计划优化
      - 在这方面比较经典的论文，推荐你读一读《展示广告的统计套利挖掘》（Statistical Arbitrage Mining for Display Advertising）[4]。从基本的思路上来讲，我们需要做的是把刚才的基于单个广告推广计划的有限制优化问题给扩展到多个广告推广计划上去。除了满足各种限制条件以外（比如需要满足总的预算要求），论文也提出了一种基于风险控制的思路，来计算每一个广告推广计划的均值和方差，从而限制方差的大小来降低风险。
      - 比较遗憾的是，论文提出的优化是一个基于 EM 算法的过程，也就是说相对于单个广告推广计划来说，多个广告推广计划找到的解可能并不是全局的最优解。（**)
      - 
### Budget Pacing

  - 在每一个时段，发布商所面临的受众都有可能不太一样，所以，对于广告商而言，比较理想的状态是一个广告可以在一天的不同时段被不同的受众所看到，从而达到扩大受众面的目的。
  - 一种叫“节流”（Throttling）
    - 节流这种方法主要是把单位时间的支出或者是成本给控制在某一个速率内，使得预算能够被均匀地使用。这种方法往往是在我们已经介绍过的竞价模型之外运行。
    - 节流思路，有一种做法[1]是把如何节流当做一种“线性优化”问题，并且是有限制的最大化问题。具体来说，对于每一个出价的请求，我们都可以做一个二元的决定，决定我们是否接受这个出价请求。当然，对于每一个出价请求，这里都有一个价值和一个成本。根据对不同出价请求的设置，我们来做优化，从而能够最大化总价值。但同时，我们需要遵守一个限制，总的成本不能超过预算。这其实就是在两种目标之间实现一个均衡，简言之，我们需要在不超过总预算的情况下达到总价值的最大化。虽然这种算法本身能够通过我们之前介绍过的“拉格朗日乘数法”来求解，
    - 但是还存在一个根本的问题，那就是这种算法并不能实时地对整个竞价的安排进行计算和更新。因为，这种线性优化方法一般都是在线下计算好了以后再到线上运行。很明显，这种方法并不适合快速变化的竞价环境。
    - 也就有一些工作[2]和[3]，尝试通过节流，或者更确切地说，通过在线优化来控制预算的使用情况。
  - 一种叫“修改出价”。
    - 修改出价这个思路很直观，也就是直接修改我们的竞价，从而带来预算均匀化的结果。
    - 竞价直接进行修改的相关工作也很多[4]和[5]，这个思路是把控制理论中的一些思想借鉴到了对竞价的直接优化上，目标是让广告商的预算能够平滑使用。这里面的控制是指什么呢？主要是指我们引入一个新的模块在 DSP 中，从而能够实时监测各种指标，例如竞价赢的比率、点击率等，然后利用这些数据作为一个参考点，从而能够形成一种回馈信息以供控制系统来对出价进行实时的调整。和节流的思想相对比，利用控制理论对出价进行直接优化这种思路明显要更加灵活。
    - 然而在实际的工作中，更加灵活的框架依赖于对点击率以及竞价全景观的准确预测，这其实是很困难的。在真实的情况下，利用节流的思想，也就是不去修改出价，只是在其基础上直接进行操作，则往往来得简单有效。
  - 频控
    - 在工业界，还有一种经常会使用的控制预算的方法叫“频率上限”（Frequency Cap）。简单来说，这种策略就是限制某一个或者某一种广告在某一种媒介上一段时间内出现的次数。比如，是否限制一个肯德基的广告在半天之内让同一个用户看见的次数？5 次、10 次还是 20 次？为什么要限制频率呢？
    - 一个因素当然是我们希望广告的预算不要在短时间内消耗完。另外，短时间内反复观看某一个广告，很可能会让用户对某一个广告或者广告商产生厌烦情绪，那么广告的有效度就会降低。这对于一些广告商来说，其实是消耗了一些资源。因此，限制广告的投放是一种策略选择，从而让广告的投放花钱少、效率高。
    - 这种频率上限的做法在工业界非常普遍，不过比较遗憾的是，关于这样做究竟是不是有很大的效果，用户多次看到广告是否会真正产生非常大的厌烦情绪从而使得广告效果降低，有没有理论支持等问题，目前还没有比较好的研究来解决。
  - Reserved Price