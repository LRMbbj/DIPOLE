<div align="center">

# Dichotomous Diffusion Policy Optimization

[Ruiming Liang\*](https://github.com/LRMbbj), [Yinan Zheng\*](https://github.com/ZhengYinan-AIR), [Kexin Zheng\*](https://air-dream.netlify.app/author/kexin-zheng/), [Tianyi Tan\*](https://github.com/0ttwhy4), [Jianxiong Li](https://facebear-ljx.github.io/), Liyuan Mao, [Zhihao Wang](https://zh1hao.wang/), Guang Chen, Hangjun Ye, [Jingjing Liu](https://air.tsinghua.edu.cn/en/info/1046/1194.htm), Jinqiao Wang$\dagger$, [Xianyuan Zhan](https://zhanxianyuan.xyz/)$\dagger$

<p align="center">
  <a href="">
    <img
      src="https://img.shields.io/badge/DIPOLE-page-blue?logo=IcoMoon&logoColor=white"
      alt="DIPOLE Website"
    />
  </a>
  <a href="">
    <img
      src="https://img.shields.io/badge/DIPOLE-Paper-red?logo=arxiv&logoColor=red"
      alt="BAGEL Paper on arXiv"
    />
  </a>
  <a href="">
    <img 
        src="https://img.shields.io/badge/DIPOLE-Model-yellow?logo=huggingface&logoColor=yellow" 
        alt="BAGEL Model"
    />
  </a>
</p>

<p align="center">
  <img src="page/images/method.svg" alt="SVG Image">
</p>

</div>

## 📢 News

- **Jan 1, 2026:** We released the official [website](), [repo]() and [paper]() for DIPOLE.

## 🔥 Quick Start

**Comming soon.**

## 📊 Benchmarks

### ExORL

Average score over 8 random seeds (w/o rs: without rejection sampling)

| Domain    | Task            | IQL      | ReBRAC  | CFGRL    | IFQL     | FQL          | DIPOLE w/o rs | **DIPOLE**   |
| --------- | --------------- | -------- | ------- | -------- | -------- | ------------ | ------------- | ------------ |
| Walker    | stand           | 603 ± 8  | 461 ± 3 | 782 ± 8  | 873 ± 6  | 801 ± 4      | 793 ± 11      | **953 ± 4**  |
| Walker    | walk            | 444 ± 4  | 208 ± 6 | 608 ± 32 | 844 ± 11 | 755 ± 12     | 679 ± 16      | **910 ± 5**  |
| Walker    | run             | 247 ± 10 | 98 ± 2  | 282 ± 6  | 406 ± 8  | 294 ± 11     | 256 ± 12      | **442 ± 9**  |
| Quadruped | walk            | 776 ± 15 | 344 ± 7 | 762 ± 25 | 883 ± 12 | 739 ± 25     | 813 ± 21      | **928 ± 55** |
| Quadruped | run             | 485 ± 7  | 344 ± 3 | 571 ± 25 | 595 ± 18 | 503 ± 5      | 560 ± 11      | **657 ± 10** |
| Cheetah   | run             | 168 ± 7  | 97 ± 13 | 216 ± 15 | 269 ± 16 | 222 ± 14     | 194 ± 9       | **274 ± 12** |
| Cheetah   | run-backward    | 146 ± 8  | 85 ± 4  | 262 ± 26 | 310 ± 24 | 231 ± 12     | 227 ± 7       | **350 ± 15** |
| Jaco      | reach-top-right | 33 ± 2   | 38 ± 13 | 72 ± 6   | 193 ± 9  | **224 ± 17** | 84 ± 5        | 117 ± 18     |
| Jaco      | reach-top-left  | 30 ± 8   | 59 ± 5  | 46 ± 6   | 181 ± 11 | **222 ± 42** | 63 ± 8        | 110 ± 12     |

### OGBench

Aggregate score over all single tasks for each category (average over 8 random seeds)

| Task Category                          | IQL    | ReBRAC | IDQL       | IFQL       | FQL        | **DIPOLE** |
| -------------------------------------- | ------ | ------ | ---------- | ---------- | ---------- | ---------- |
| humanoidmaze-medium-navigate (5 tasks) | 33 ± 2 | 2 ± 8  | 1 ± 0      | 60 ± 14    | 58 ± 5     | **68 ± 3** |
| humanoidmaze-large-navigate (5 tasks)  | 2 ± 1  | 2 ± 1  | 1 ± 0      | **11 ± 2** | 4 ± 2      | 6 ± 2      |
| antsoccer-arena-navigate (5 tasks)     | 8 ± 2  | 0 ± 0  | 12 ± 4     | 33 ± 6     | **60 ± 2** | **57 ± 7** |
| cube-single-play (5 tasks)             | 83 ± 3 | 91 ± 2 | **95 ± 2** | 79 ± 2     | **96 ± 1** | **97 ± 2** |
| cube-double-play (5 tasks)             | 7 ± 1  | 12 ± 1 | 15 ± 6     | 14 ± 3     | 29 ± 2     | **44 ± 7** |
| scene-play (5 tasks)                   | 28 ± 1 | 41 ± 3 | 46 ± 3     | 30 ± 3     | 56 ± 2     | **60 ± 2** |

### NavSim

| Method                               | Input       | NC↑  | DAC↑ | TTC↑ | Comf.↑ | EP↑  | **PDMS↑** |
| ------------------------------------ | ----------- | ---- | ---- | ---- | ------ | ---- | --------- |
| Constant Velocity                    | -           | 68.0 | 57.8 | 50.0 | 100.0  | 19.4 | 20.6      |
| Ego Status MLP                       | -           | 93.0 | 77.3 | 83.6 | 100.0  | 62.8 | 65.6      |
| UniAD                                | Cam         | 97.8 | 91.9 | 92.9 | 100.0  | 78.8 | 83.4      |
| PARA-Drive                           | Cam         | 97.9 | 92.4 | 93.0 | 99.8   | 79.3 | 84.0      |
| LFT                                  | Cam         | 97.4 | 92.8 | 92.4 | 100.0  | 79.0 | 83.8      |
| Transfuser                           | Cam & Lidar | 97.7 | 92.8 | 92.8 | 100.0  | 79.2 | 84.0      |
| Hydra-MDP                            | Cam & Lidar | 98.3 | 96.0 | 94.6 | 100.0  | 78.7 | 86.5      |
| **DP-VLA (ours)**                    | Cam         | 98.0 | 97.0 | 94.3 | 100.0  | 82.5 | **88.3**  |
| **DP-VLA w/ DIPOLE navtrain (ours)** | Cam         | 98.2 | 98.0 | 95.2 | 100.0  | 83.6 | 89.7      |
| DP-VLA w/ DPPO navtest               | Cam         | 97.9 | 97.6 | 94.1 | 100.0  | 83.5 | 89.0      |
| **DP-VLA w/ DIPOLE navtest (ours)**  | Cam         | 99.2 | 98.7 | 95.6 | 99.8   | 94.2 | **94.8**  |

## ✍️ Citation

```bibtex

```
