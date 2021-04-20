---
title: [RIS-explore] 2021/4/20 文献调研
date: 2021-04-18 23:05:43
tags: [latex, paper, IEEE]
categories:
    - paper
    - RIS
	- Explore
index_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203815.png
banner_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203849.png
comment: true
---

![I don't Fucking care! - spongebob rainbow | Meme Generator](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/41118275.jpg)

目前在寻找和智能反射表面（Reconfigurable Intelligent Surface）有关的学术方向来~~水论文~~进行研究。之前进行过一篇RIS和UAV（Unmanned Arial Vehicle）结合的安全通信相关的文章，标题为：

> Learning-based Robust and Secure Transmission for Reconfigurable Intelligent Surface Aided Millimeter Wave UAV Communications

基本上都是在follow别人的工作：

1、***H.  Yang,  Z.  Xiong,  J.  Zhao,  D.  Niyato,  L.  Xiao,  and  Q.  Wu,  “Deep reinforcement  learning-based  intelligent  reflecting  surface  for  securewireless  communications,” IEEE Trans. Wireless Commun.,  vol.  20,no. 1, pp. 375–388, Jan. 2021.***

该文章使用深度强化学习（Deep Reinforcement Learning）的方法来求解RIS辅助BS（base station）通信中的主被动波束赋形的问题，由于考虑了窃听者所以设计方案的复杂度会相应的增长。

还有一点就是该文章中提出了由于移动性产生的信道误差的模型。具体来讲，BS端获取到的CSI（channel state information）已经是经过了传输和处理等过程，其实已经过时，过时的CSI和当前的真正的CSI会不一样，也就是说BS处通过过时的CSI得出的优化方案并不是最优的，该模型被很多文章沿用。
$$
\boldsymbol{h}\left(t+T_{\mathrm{d}}\right)=\varrho \tilde{\boldsymbol{h}}(t)+\sqrt{1-\varrho^{2}} \Delta \boldsymbol{h}
$$
其中$\varrho$是过时CSI和实时CSI之间的（自）相关系数，其物理意义为过时CSI和实时CSI之间的相关程度，相关程度越高，实时到过时的信息损失就越小，其表达式为零阶贝塞尔函数：
$$
\varrho=J_{0}\left(2 \pi f_{D} T_{\mathrm{d}}\right)
$$
其中，$f_{D}=v f_{c} / c$

同时，还借鉴了其中的安全通信速率的概念。这一点直接引用，并没有经过深入推导。
$$
R_{k}^{\mathrm{sec}}=\left[R_{k}^{\mathrm{u}}-\max _{\forall p} R_{p, k}^{\mathrm{e}}\right]^{+}
$$


2、***X.  Liu,  Y.  Liu,  and  Y.  Chen,  “Machine  learning  empowered  trajectoryand passive beamforming design in UAV-RIS wireless networks,”IEEEJ. Sel. Areas Commun., Dec. 2020, accepted to appear.***

该文章研究了RIS辅助的UAV通信系统，作者假设在这样的系统中UAV的传输过程和移动过程是分割开的。该UAV在移动过程中不会进行信息传输，只有在移动到合适位置时才会进行传输

该文章中使用了一种UAV能量消耗模型，也许在将来可以借鉴
$$
\begin{aligned}
\bar{E}(t)=& \frac{1}{T_{r}} \cdot \sum_{t=n T_{r}}^{(n+1) T_{r}} E_{b}\left(1+\frac{3 v^{2}(t)}{U_{\mathrm{tip}}^{2}}\right)+\frac{1}{T_{r}} \cdot \sum_{t=n T_{r}}^{(n+1) T_{r}} E_{i}\left(\sqrt{1+\frac{v^{4}(t)}{4 v_{0}^{4}}}-\frac{v^{2}(t)}{2 v_{0}^{2}}\right) \\
&+\frac{1}{T_{r}} \cdot \sum_{t=n T_{r}}^{(n+1) T_{r}} \frac{1}{2} f_{d} \rho s A v^{3}(t)
\end{aligned}
$$
3、***3GPP, “Study on channel model for frequencies from 0.5 to 100 GHz,”3rd Generation Partnership Project (3GPP), Technical Specification (TS)38.901, 01 2020, version 16.1.0.***

这是3gpp在0.5GHz到100GHz信道建模时给出的标准，其中的AoD和AoA的模型是参考标准

![image-20210420202203778](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210420202203778.png)

4、***G.  Zhou,  C.  Pan,  H.  Ren,  K.  Wang,  M.  Elkashlan,  and  M.  D.  Renzo,“Stochastic  learning-based  robust  beamforming  design  for  RIS-aided millimeter-wave  systems  in  the  presence  of  random  blockages,”IEEE Trans. Veh. Technol., Jan. 2021, accepted to appear.***

毫米波信道在该文章中被考虑，毫米波信道建模同城被称作SalehValenzuela信道
$$
\begin{aligned}
\mathbf{h}_{\mathrm{b}, k} &=\sqrt{\frac{1}{L_{B U}}} \sum_{l=1}^{L_{B U}} g_{k, l}^{\mathrm{b}} \mathbf{a}_{L}\left(\theta_{k, l}^{\mathrm{b}, t}\right), \forall k \in \mathcal{K}, \\
\mathbf{h}_{\mathrm{i}, k} &=\sqrt{\frac{1}{L_{I U}}} \sum_{l=1}^{L_{I U}} g_{k, l}^{\mathrm{i}} \mathbf{a}_{P}\left(\theta_{k, l}^{\mathrm{i}, t}, \phi_{k, l}^{\mathrm{i}, t}\right), \forall k \in \mathcal{K} \\
\mathbf{H}_{\mathrm{bi}} &=\sqrt{\frac{1}{L_{B I}}} \sum_{l=1}^{L_{B I}} g_{l}^{\mathrm{bi}} \mathbf{a}_{P}\left(\theta_{l}^{\mathrm{i}, r}, \phi_{l}^{\mathrm{i}, r}\right) \mathbf{a}_{L}\left(\theta_{l}^{\mathrm{b}, t}\right)^{\mathrm{H}}
\end{aligned}
$$
