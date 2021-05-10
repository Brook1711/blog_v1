---
title: active RIS  文献调研 1
date: 2021-05-10 10:05:43
tags: [latex, paper, IEEE]
categories:
    - paper
    - RIS
	- active RIS
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/41118275.jpg
banner_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203849.png
comment: true
---

# Active RIS vs. Passive RIS: Which Will Prevail in 6G?

https://arxiv.org/pdf/2103.15154.pdf
<br/>阅读目的：其中提到了反射元对幅度的增幅模型，即，（activate RIS）

## abstract

> From 1G to 5G, wireless channels have been traditionally considered to be uncontrollable. Thanks to the recent advances in meta-materials, reconfigurable intelligent surfaces (RISs) <mark>have emerged as a new paradigm</mark> for controlling wireless channels intelligently, thus making it a revolutionary technique for future 6G wireless communications. However, due to the <mark>“double fading” effect</mark>, RIS only achieves a <mark>negligible capacity gain</mark> in typical communication scenarios, which however has been widely ignored in many existing works. In this paper, the concept of active RIS is proposed to break this fundamental physical limit. Different from the existing passive RIS that reflects signals passively without amplification, active RIS can actively amplify the reflected signals. We then develop a signal model for active RIS, which is validated through experimental measurements. Based on this new signal model, we analyze the capacity gain  chievable by active RIS and formulate the capacity maximization problem in an active RIS aided system. Next, a joint transmit and reflect precoding algorithm is proposed to solve this problem. Finally, extensive results show that, compared with the baseline without RIS, the existing passive RIS can realize a negligible capacity gain of only 3% in typical application scenarios, while the proposed active RIS can achieve a noticeable capacity gain of 129%, thus overcoming the fundamental limit of “double fading” effect.
> <br/>“双衰落”导致RIS的辅助增益极低

从1G到5G，传统观点上认为无线信道是不可以控制的。但是由于最近超材料（meta-material）的发展，可重构智能表面（RIS）已经成为智能控制无线信道的新范例，从而使其成为未来6G无线通信的革命性技术。 但是，由于“双重衰落”效应，RIS在典型的通信情况下只能实现微不足道的容量增益，但是在许多现有工作中却被广泛忽略。 在这篇文章中，提出了主动RIS的概念以打破这一基本物理限制。和现有的只是被动的反射信号不同，主动RIS可以主动增幅反射信号。我们随之建立了主动RIS的信号模型，该模型通过实验测量已经被证实。基于这种新的信号模型，我们分析了有源RIS可实现的容量增益，并提出了有源RIS辅助系统中的容量最大化问题。接下来，提出了一种联合发射和反射的预编码算法来解决这个问题。最后，广泛的结果表明，与不使用RIS的基线相比，现有的被动RIS在典型应用方案中只能实现3％的可忽略不计的容量增长，而建议的主动RIS可以实现129％的显着容量增长，因此可以克服 “双重衰落”效应的根本极限。


## introduction

> Over the past few decades, wireless communications have provided society with significant benefits. From 1G to 5G, the system capacity has been significantly improved by advancing the transceiver design, while the wireless channels have been usually considered to be uncontrollable. Recently, with the interdisciplinary development of meta-materials, electromagnetics, and wireless communications, a revolutionary technique called reconfigurable intelligent surface (RIS) has been proposed [1]–[4], which offers a novel design paradigm by adding new degrees of freedom to intelligently control wireless channels for improved communications. Specifically, an RIS is an array composed of massive passive elements, which reflect electromagnetic signals in a desired manner so as to reconfigure the wireless environment [5]. Thanks to its high array gain, low cost, low power, and <mark>low noise</mark> [5]– [7], RIS is expected to improve channel capacity [8], extend coverage [9], and reduce power consumption [10] for future 6G communications. Additionally, RISs are projected to have other applications such as in WiFi [11], precision measurement [12], and navigation [13].
> <br/><mark>低噪声的特性之前没有见过</mark>

在过去的几十年中，无线通信为社会带来了巨大的进步。 从1G到5G，先进的收发器设计大大提高了系统容量，而通常认为无线通道是不可控制的。近年来，随着超材料，电磁学和无线通信的跨学科发展，提出了一种革命性的技术，称为可重构智能表面（RIS）[1] – [4]，它通过增加新的自由度提供了一种新颖的设计范例。 智能控制无线信道以改善通信。具体地说，RIS是由大量无源元件组成的阵列，这些元件以所需的方式反射电磁信号，从而重新配置无线环境。由于其高阵列增益，低成本，低功耗和低噪声[5] – [7]，RIS有望在未来6G通信中提高信道容量[8]，扩展覆盖范围[9]和降低功耗[10]。此外，RIS预计将有望在其他场景中得到应用，例如WiFi [11]，精度测量[12]和导航[13]。

> Due to the negligible noise introduced by passive RISs, one of the most essential benefits of RISs is the <mark>“square law” array gain</mark>. In particular, the array gain of an $N$-element RIS is proportional to $N^2$ , which is N times larger than that achievable by the standard massive multiple-input multiple output (MIMO) [5]. Benefiting from this advantage, RIS is expected to bring significant capacity gains in future 6G wireless networks. <mark>However, actually significant capacity gains are only observed in atypical communication scenarios where the direct link from the transmitter to the receiver is completely blocked or very weak [8]–[10], [14]–[16].</mark> By contrast, in the typical scenario where the direct link is not weak, the common RISs with hundreds of passive elements can only achieve negligible capacity gains [17]. The reason behind this phenomenon is the “double fading” effect introduced by RIS, i.e., the signals received via the reflection link <mark>suffer from large-scale fading twice</mark>. Particularly, the equivalent path loss of the transmitter RIS-receiver link is the product (instead of the summation) of the path losses of the transmitter-RIS link and RIS-receiver link, which is usually thousands of times larger than that of the direct link [17]. As a result, the “double fading” effect makes it almost impossible for passive RIS to achieve a noticeable capacity gain in typical wireless environment. Most existing works on RIS have bypassed this effect by only considering atypical scenarios with very poor direct links [8]–[10], [14]– [16]. Therefore, to advance the practicability of RIS for future 6G wireless networks, a critical issue must to be addressed is: How to overcome the fundamental limit of “double fading” effect of RIS?
> <br/> RIS的特性——<mark>“平方律增益”</mark>（square law）

由于无源RIS引入的噪声可忽略不计，所以RIS的最基本好处之一就是“平方律”阵列增益。特别是，N元素RIS的阵列增益与N 2成正比，这比标准大规模多输入多输出（MIMO）可获得的阵列增益大N倍[5]。受益于此优势，RIS有望在未来的6G无线网络中带来巨大的容量增长。但是，实际上只有在非典型的通信场景中才能观察到显着的容量增益，其中从发射机到接收机的直接链路被完全阻塞或非常弱[8] – [10]，[14] – [16]。相比之下，在直接链路不弱的典型情况下，具有数百个无源元件的普通RIS只能获得微不足道的容量增益[17]。这种现象背后的原因是RIS引入的“双重衰落”效应，即通过反射链路接收的信号两次遭受大规模衰落。特别是，发射机RIS-接收机链路的等效路径损耗是发射机-RIS链路和RIS-接收机链路的路径损耗的乘积（而不是总和），通常比直接链路的路径损耗大数千倍。链接[17]。结果，“双衰落”效应使得无源RIS在典型的无线环境中几乎不可能获得明显的容量增益。现有的大多数关于RIS的著作都只考虑了具有非常差的直接联系的非典型场景[8]-[10]，[14]-[16]，从而绕过了这种影响。因此，要提高RIS在未来6G无线网络中的实用性，必须解决的关键问题是：如何克服RIS的“双重衰落”效应的基本限制？

>To break the fundamental physical limit of the “double fading” effect, the new concept of active RIS is proposed in this paper. Specifically, our contributions are summarized as follows: 
><br/>• We propose the concept of active RIS to overcome the “double fading” effect in typical communication scenarios. Different from the existing passive RIS that just passively reflects signals without amplification, the key feature of active RIS is the capability of actively reflectin g signals with amplification at the expense of additional power consumption. 
><br/>• We develop a new signal model for the proposed active RIS, which characterizes how the incident signal is amplified and how <mark>non-negligible thermal noise</mark> is introduced at the active elements. Particularly, an active RIS element was designed and fabricated to validate the developed signal model through experimental measurements. 
><br/>• Based on the proposed signal model, we analyze the capacity gain achievable by active RISs and formulate a capacity maximization problem in an active RIS aided MIMO system. Then, a joint transmit and reflect precoding algorithm is proposed to solve this problem. Extensive results show that, in a typical communication scenario, the existing passive RIS only achieves a negligible ca pacity gain of 3%, while the proposed active RIS is able to achieve a noticeable capacity gain of 129%, thus overcoming the fundamental limit of “double fading” effect.
><br/>在主动RIS中考虑了热噪声

为了打破“双衰落”效应的基本物理极限，本文提出了有源RIS的新概念。具体来说，我们的贡献总结如下：
<br/>•我们提出了主动RIS的概念，以克服典型通信场景中的“双衰落”效应。不同于现有的被动RIS只是被动地反射信号而不进行放大，主动RIS的关键特征是能够通过放大来主动反射信号，但要付出额外的功耗。
<br/>•我们为拟议的有源RIS开发了一个新的信号模型，该模型描述了入射信号如何放大以及如何在有源元件处引入不可忽略的热噪声。特别是，设计并制造了有源RIS元件，以通过实验测量来验证开发的信号模型。
<br/>•基于提出的信号模型，我们分析了有源RIS可获得的容量增益，并提出了有源RIS辅助MIMO系统中的容量最大化问题。然后，提出了一种联合发射和反射的预编码算法来解决这个问题。广泛的结果表明，在典型的通信场景中，现有的被动RIS只能实现3％的可忽略不计的容量增益，而建议的主动RIS能够实现129％的显着容量增益，从而克服了“双重衰落”效果。

> The rest of this paper is organized as follows. In Section II, the concept of active RIS is introduced and its impact on channel capacity is analyzed. Then, the proposed joint precoding design for capacity maximization is provided in Section III. In Section IV, the results of experimental measurements and numerical simulations are presented. Finally, conclusions are drawn and future works are discussed in Section V. Notations: C and R+ denote the sets of complex and positive real numbers, respectively; [·] −1 , [·] T , and [·] H denote the inverse, transpose, and conjugate-transpose operations, respectively; k· k denotes the Euclidean norm of its argument; diag(·) denotes diagonal operation; R{·} denotes the real part of its argument; ⊗ denotes the Kronecker product; ∠[·] denotes the angle of its complex argument; ln(·) denotes the natural logarithm of its argument; CN (µ, Σ) denotes the complex multivariate Gaussian distribution with mean µ and variance Σ; IL is an L × L identity matrix, and 0L is an L × 1 zero vecto

# 可借鉴的点

## 对于传统RIS“double fading”的阐述

>  However, due to the <mark>“double fading” effect</mark>, RIS only achieves a <mark>negligible capacity gain</mark> in typical communication scenarios, which however has been widely ignored in many existing works.

> <mark>However, actually significant capacity gains are only observed in atypical communication scenarios where the direct link from the transmitter to the receiver is completely blocked or very weak [8]–[10], [14]–[16].</mark> By contrast, in the typical scenario where the direct link is not weak, the common RISs with hundreds of passive elements can only achieve negligible capacity gains [17]. The reason behind this phenomenon is the “double fading” effect introduced by RIS, i.e., the signals received via the reflection link <mark>suffer from large-scale fading twice</mark>. Particularly, the equivalent path loss of the transmitter RIS-receiver link is the product (instead of the summation) of the path losses of the transmitter-RIS link and RIS-receiver link, which is usually thousands of times larger than that of the direct link [17]. As a result, the “double fading” effect makes it almost impossible for passive RIS to achieve a noticeable capacity gain in typical wireless environment. 


## 关于平方律增益“square law array gain”的叙述

> Due to the negligible noise introduced by passive RISs, one of the most essential benefits of RISs is the <mark>“square law” array gain</mark>.


## 传统RIS大规模反射器件造成的问题的阐述

>Due to the high overhead of N pilots for channel estimation [20] and the high complexity of O(N2 ) for real-time beamforming [21], such a large number of RIS elements makes the application of passive RIS in practical wireless networks almost impossible [17]. Consequently, most existing works have bypassed the “double fading” effect by only considering the atypical scenario where the direct link is completely blocked or very weak [5]–[10], [14]–[16].


## active RIS的硬件实现方法：

> To achieve this goal, the key component of an active RIS element is the additionally integrated active reflection type amplifier, which can be realized by many existing active components, such the current-inverting converter [22],the asymmetric current mirror [23], or even some integrated chips [24].


## 与RF-RIS和FD-AF delay的不同

>It should be noted that, the proposed active RIS is fundamentally different from the RIS equipped with active radio frequency (RF) components [25], [26]. Specifically, some passive RIS elements are connected to additional active RF chains, which are used for baseband signal processing. In this way, these RIS elements are enabled to have the signal processing capabilities [25], [26]. On the contrary, the proposed active RIS has no these capabilities, which only reflects and amplifies the incident signal to strengthen the reflection link. Besides, although the proposed active RIS can amplify the incident signal, which is similar to the full-duplex amplify-and-forward (FD-AF) relay, their hardware structures and transmission models are actually quite different. Specifically, FD-AF relay is equipped with RF chains to receive the incident signal and then transmit it after amplification [27]. Due to the long delay of this process, it takes two time slots to complete the transmission of a symbol, and the received signal at the receiver in a time slot actually carries two different symbols, which are transmitted by the transmitter and the FD-AF relay, respectively [27]. Thus, FD-AF has two different transmission models in two adjacent time slots [27, Eq. (22), Eq. (25)], while the proposed active RIS has only one transmission model (3) in every time slot.

## activate RIS的基本信号模型

>With the reflection-type amplifier supported by a power supply, the reflected and amplified signal of an N-element active RIS can be modeled as follows:

$$
\mathbf{y}=\underbrace{\mathbf{P} \boldsymbol{\Theta} \mathbf{x}}_{\text {Desired signals }}+\underbrace{\mathbf{P \Theta} \mathbf{v}}_{\text {Dynamic noise }}+\underbrace{\mathbf{n}_{\mathrm{s}}}_{\text {Static noise }},
$$

where $x\in \mathbb{C}^N$ denotes the incident signal, $\Theta \triangleq \operatorname{diag}\left(e^{j \theta_{1}}, \cdots, e^{j \theta_{N}}\right) \in \mathbb{C}^{N \times N}$ denotes the phase shift matrix of the RIS, $\mathbf{y} \in \mathbb{C}^N$ denotes the signal reflected by the RIS, $\mathbf{P} \triangleq \operatorname{diag}\left(p_{1}, \cdots, p_{N}\right) \in \mathbb{R}_{+}^{N \times N}$, wherein each element can be larger than one thanks to the integrated active amplifier. Due to the use of active components, active RISs consume additional power to amplify the reflected signals, and the thermal noise introduced by active RIS elements cannot be ignored as is done for passive RIS.  Particularly, as shown in (2), the introduced noises can be divided into dynamic noise and static noise [23]. Specifically, $\mathbf{v}$ is related to the input noise and noise factor of the active RIS elements [23], while the static noise $\mathbf{n}_\text{s}$ is unrelated to $\mathbf{P}$ and is usually negligible compared with the dynamic noise $\mathbf{P} \Theta \mathbf{v}$ [23]. Without loss of generality, here we assume $\mathbf{v} \sim \mathcal{C} \mathcal{N}\left(\mathbf{0}_{N}, \sigma_{v}^{2} \mathbf{I}_{N}\right)$
<br/> &emsp;Then, we consider an active RIS aided multiple-input multiple-output (MIMO) system, where an $M$-antenna base station (BS) simultaneously serve $K$ single-antenna users with the aid of an $N$-element active RIS. Therefore, according to (2), the signal $r_k \in \mathbb{C}$ received at user $k$ can be modeled as
$$
r_{k}=(\underbrace{\mathbf{h}_{k}^{H}}_{\text {Direct link }}+\underbrace{\mathbf{f}_{k}^{H} \mathbf{P} \boldsymbol{\Theta} \mathbf{G}}_{\text {Reflection link }}) \sum_{j=1}^{K} \mathbf{w}_{j} s_{j}+\underbrace{\mathbf{f}_{k}^{H} \mathbf{P} \mathbf{\Theta} \mathbf{v}}_{\text {Noises introduced at active RIS }}+\underbrace{z_{k}}_{\text {Noise introduced at user } k}
$$
where $\mathbf{s} \triangleq\left[s_{1}, \cdots, s_{K}\right]^{T} \in \mathbb{C}^{K}$ denote the transmitted symbols for $K$ users with normalized power; $G \in \mathbb{C}^{N\times M}$, $\mathbf{h}_{k}^{H} \in \mathbb{C}^{1 \times M}$, and $\mathbf{f}_{k}^{H} \in \mathbb{C}^{1 \times N}$ denote the channels from BS to RIS, from BS to user $k$, and from RIS to user $k$, respectively; $\mathbf{w}_{k} \in \mathbb{C}^{M \times 1}$ denotes the BS beamforming vector for $s_k$; $z_k$ denotes the additive white Gaussion noise (AWGN) at the user and here we assume $z_{k} \sim \mathcal{C} \mathcal{N}\left(0, \sigma^{2}\right)$.

## SISO 场景的activate RIS

> We consider to analyze the capacity gain achievable by active RIS by studying the user’s achievable SNR in a simple SISO scenario. To focus on the capacity gain provided by the active RIS aided reflection link, <mark>we ignore the direct link by setting $\mathbf{h}_{k} \triangleq 0$ [28]. For simplicity, we assume that every active RIS element has the same amplification factor ($p_{n} \triangleq p,\forall n \in\{1, \cdots, N\}$)</mark>, and redefine G , g = [g1, · · · , gN ] T , fk , f = [f1, · · · , fN ] T , and wk , w. Then, according to (3), the maximization of the user’s SNR γ subject to the power constraints at the BS and active RIS can be formulated as follows

