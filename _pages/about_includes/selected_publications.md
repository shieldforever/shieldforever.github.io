# 📝 Selected Publications 


<div class='paper-box'><div class='paper-box-image'><div><div class="badge"><strong>HPCA 2026</strong></div><img src='images/orange-hpca26.jpg' alt="ORANGE" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

<a href="https://www.lihaomin.com/" style="color: #224b8d; "><strong>
  ORANGE: Exploring Ockham’s Razor for Neural Rendering by Accelerating 3DGS on NPUs with GEMM-Friendly Blending and Balanced Workloads</strong>
</a>
<br>
**Haomin Li**, Yue Liang, Fangxin Liu, Bowen Zhu, Zongwu Wang, Yu Feng, Liqiang Lu, Li Jiang, and Haibing Guan
<br>
**Description**: ORANGE is a novel approach that enables general purpose DNN-oriented Neural Processing Units (NPUs) to execute 3DGS without requiring specialized acclerators. Our approach offers a cost-effective and versatile solution, adhering to the principle of Ockham’s Razor by maximizing efficiency without specialized hardware.
</div>
</div>



<div class='paper-box'><div class='paper-box-image'><div><div class="badge"><strong>ASPLOS 2025</strong></div><img src='images/asdr-asplos25.jpg' alt="ASDR" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

<a href="https://dl.acm.org/doi/10.1145/3676642.3736117" style="color: #224b8d; "><strong>
  ASDR: Exploiting <u>A</u>daptive <u>S</u>ampling and <u>D</u>ata <u>R</u>euse for CIM-based Instant Neural Rendering</strong>
</a>
<br>
Fangxin Liu=, **Haomin Li=**, Bowen Zhu, Zongwu Wang, Zhuoran Song, and Li Jiang
<br>
**Description**: ASDR is a CIM-based accelerator supporting efficient neural rendering. At the algorithmic level, we propose two rendering optimization schemes: (1) Dynamic sampling by online sensing of the rendering difficulty of different pixels, thus reducing access memory and computational overhead. (2) Reducing MLP overhead by decoupling and approximating the volume rendering of color and density. At the architecture level, we design an efficient ReRAM-based CIM architecture with efficient data mapping and reuse microarchitecture.
</div>
</div>



<div class='paper-box'><div class='paper-box-image'><div><div class="badge"><strong>ISCA 2025</strong></div><img src='images/fate-isca25.jpg' alt="FATE" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

<a href="https://dl.acm.org/doi/10.1145/3695053.3731031" style="color: #224b8d; "><strong>
  FATE: Boosting the Performance of Hyper-Dimensional Computing Intelligence with <u>F</u>lexible Numerical <u>DA</u>ta Typ<u>E</u></strong>
</a>
<br>
**Haomin Li**, Fangxin Liu, Yichi Chen, Zongwu Wang, Shiyuan Huang, Ning Yang, Dongxu Lyu, and Li Jiang
<br>
**Description**:  FATE is an algorithm/architecture co-designed solution for brain-inspired Hyper-Dimensional Computing (HDC) deployment, which utilizes low-precision data types for less important dimensions, enabling the replacement of multiplication operations with logic calculations. To maximize resource utilization, we design a workload-aware mixed quantization scheme that offers flexible compression based on these differences in dimensional importance. The proposed quantization framework is seamlessly integrated into the existing FPGA implementations.
</div>
</div>



<div class='paper-box'><div class='paper-box-image'><div><div class="badge"><strong>TACO 2025 & DAC 2023</strong></div><img src='images/hyperdefense-taco25.jpg' alt="HyperAttack and HyperDefense" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

<a href="https://dl.acm.org/doi/10.1145/3736172" style="color: #224b8d; "><strong>
  Attack and Defense: Enhancing Robustness of Binary Hyper-Dimensional Computing</strong>
</a>
<br>
**Haomin Li**, Fangxin Liu, Zongwu Wang, Ning Yang, Shiyuan Huang, Xiaoyao Liang, and Li Jiang
<br>
**Description**:  
Hyper-Dimensional Computing (HDC) has emerged as a lightweight computational model, renowned for its robust and efficient learning capabilities, particularly suitable for resource-constrained hardware. As HDC often finds its application in edge devices, the associated security challenges pose a critical concern that cannot be ignored. In this work, we aim to quantitatively delve into the robustness of binary HDC, which is widely recognized for its robustness. Employing the bit-flip attack as our initial focal point, we meticulously devise both an attack mechanism (HyperAttack) and a corresponding defense mechanism (HyperDefense). Our objective is to comprehensively explore the robustness of the binary hyper-dimensional computation model, aiming to gain a deeper understanding of its security vulnerabilities and potential defenses.
<!-- HyperAttack is a novel attack framework for HDC, capable of compromising a robust binary HDC model by maliciously flipping a minimal number of bits within its memory system (specifically, the DRAM) that houses the associative memory. HyperAttack optimizes the accuracy degradation by pinpointing the most vulnerable bits in the hyper-dimensional vectors of the HDC model. The proposed HyperAttack framework is grounded in the principles of fuzziness, seamlessly integrating dimensional ranking and feature similarity analysis within hypervectors to precisely identify the bits to be flipped. Furthermore, we have developed a defense mechanism named HyperDefense, designed to bolster the robustness of binary hyper-dimensional computational models against bit-flip attacks. This defense scheme is tailored specifically for HDC models, providing a robust safeguard against potential threats. HyperDefense operates directly on the associative memory of HDC models, strengthening their defenses. By meticulously modifying selected bits, HyperDefense maintains a high level of accuracy close to the original model, even in the face of increased bit flip rates. This defense mechanism leverages redundant dimensions as backups for critical information. Through a thorough analysis of dimension importance, HyperDefense achieves superior robustness by gracefully sacrificing non-critical dimensions, thus ensuring the model’s robustness against potential attacks. -->
</div>
</div>



<div class='paper-box'><div class='paper-box-image'><div><div class="badge"><strong>DAC 2025</strong></div><img src='images/allmod-dac25.jpg' alt="ALLMod" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

<a href="https://ieeexplore.ieee.org/document/11132815" style="color: #224b8d; "><strong>
  ALLMod: Exploring Area-Efficiency of LUT-based Large Number Modular Reduction via Hybrid Workloads</strong>
</a>
<br>
Fangxin Liu=, **Haomin Li=**, Zongwu Wang, Bo Zhang, Mingzhe Zhang, Shoumeng Yan, and Li Jiang
<br>
**Description**:  
Modular reduction is widely used in cryptographic applications. High-bit-width operations are crucial for enhancing security; however, they are computationally intensive due to the large number of modular operations required. The LUT-based approach, a “space-for-time” technique, reduces computational load by segmenting the input number into smaller bit groups, pre-computing modular reduction results for each segment, and storing these results in LUTs. While effective, this method incurs significant hardware overhead due to extensive LUT usage. In this paper, we introduce ALLMod, a novel approach that improves the area efficiency of LUT-based largenumber modular reduction by employing hybrid workloads. Inspired by the iterative method, ALLMod splits the bit groups into two distinct workloads, achieving lower area costs without compromising throughput. We first develop a template to facilitate workload splitting and ensure balanced distribution. Then, we conduct design space exploration to evaluate the optimal timing for fusing workload results, enabling us to identify the most efficient design under specific constraints.
</div>
</div>


