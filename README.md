# TI Cup 2023 National Undergraduate Electronic Design Contest (NUEDC)

**Award:** Third Prize, Beijing Regional Division  
**Role:** Embedded Signal Processing & System Implementation

This project focuses on real-time signal acquisition, frequency spectrum analysis using FFT, signal separation via digital FIR filters, dual-channel DAC reconstruction, and TFT-LCD visualization — all implemented on an STM32F407 platform.

**项目中文名称**：基于STM32的混频信号分离与还原系统  
**比赛题目**：信号分离装置（H题）

## 项目概述

本系统以 **STM32F407** 为核心控制芯片，对输入的两路信号进行加法混合后，通过调用 **CMSIS-DSP** 库的 FFT 分析频谱成分，再利用预先设计的 **数字FIR滤波器** 进行频率分辨与分离处理，最后通过 **DAC** 还原出原始的两路模拟信号。同时集成 **TFT-LCD** 显示模块，可实时显示输入信号的频谱成分。

系统主要模块包括：
- 加法器电路（反相加法，使用运放实现）
- ADC 采样 + FFT 频谱分析
- FIR 数字滤波器组（Kaiser窗，MATLAB 生成系数）
- DAC 双通道输出
- 电源模块（干电池 + LM317/LM7905 稳压至 ±5V）
- TFT-LCD 显示（128×160）

关键词：**FFT** | **FIR 数字滤波器** | **ADC 采样** | **DAC 还原** | **CMSIS-DSP**

## 技术贡献 | Technical Contributions

- 利用 **CMSIS-DSP** 库的 `arm_rfft_fast_f32` 等函数实现实时频谱分析
- 通过峰值检测自动识别混频信号中的两个主要频率成分
- 设计多组带通FIR滤波器（MATLAB Filter Designer 生成），实现信号分离
- 双通道 **DAC** 还原分离后的模拟信号
- 实现从 ADC 采样 → FFT → 滤波 → DAC 的完整实时处理流水线
- TFT-LCD 显示波形与频谱（直观展示分离效果）
- 通过缓冲区与任务优化保证嵌入式平台的实时性

## 文件说明 | Files in this Repo

本仓库主要用于归档比赛成果材料，便于查阅与分享：

- **[NUEDC_Award.png](./NUEDC_Award.png)**  
  2023 年全国大学生电子设计竞赛（TI杯）北京赛区三等奖获奖证书

- **[B23212s.pdf](./B23212s.pdf)**  
  完整比赛设计报告（中文，7页），包含系统方案、理论分析、程序设计、测试结果等  

## 报告摘要（中文）

> 本系统以 STM32F407 为核心控制芯片，对输入的信号相加混合之后，调用 DSP 库中的 FFT 分析频谱成分，之后通过预先设计好的数字 FIR 滤波器，进行分辨和分离处理。最后通过 DAC 还原出两路信号。另外，本系统添加了 TFT-LCD 显示模块，可以直观显示出频谱成分。  
> 本系统主要有五个模块组成：加法器电路、采样滤波输出模块、电源电路模块、单片机控制电路及显示模块。其中电源模块达到使用移动电源供电要求，由两节干电池供电。  
> **关键词**：FFT; FIR 数字滤波器; ADC 采样; DAC 还原；DSP 库

（报告完整内容见 → **[B23212s.pdf](./B23212s.pdf)**）
