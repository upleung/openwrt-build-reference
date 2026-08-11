# openwrt-build-reference

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
![Status](https://img.shields.io/badge/Status-Active-blue.svg)
![Platform](https://img.shields.io/badge/Platform-Multi--Router-orange.svg)
![OpenWrt](https://img.shields.io/badge/OpenWrt-Reference%20Library-red.svg)
![GitHub Repo Size](https://img.shields.io/github/repo-size/NetX/openwrt-build-reference.svg)

---

## 📘 About This Project

**openwrt-build-reference** 是一个面向多硬件路由器的 **OpenWrt 编译引用库（Reference Library）**，用于集中存放构建固件所需的：

- 上游源码引用（防止仓库被删除或变为私有）
- 固件构建工具（AmlImg、u-boot、打包工具等）
- 补丁、依赖、SDK、工具链
- 各硬件型号的编译资料、脚本、配置文件
- GitHub Actions 构建引用文件（如 amlogic、ramips、bcm53xx、x86 等）

本仓库的目标是：

### ✔ 让 OpenWrt 编译更稳定  
避免上游仓库失效导致构建失败。

### ✔ 让多硬件构建更高效  
所有资料集中管理，构建脚本可直接引用。

### ✔ 让资料长期可用  
作为公共镜像库，确保工具与源码不会丢失。

---

## 🔧 Included Tools & References

本仓库将长期维护以下内容：

### **📌 固件构建工具**
- AmlImg（OneCloud 烧录工具）
- u-boot（各硬件型号）
- 打包工具（img、ext4、sparse 等）
- 编译依赖（android-sdk-libsparse-utils 等）

### **📌 上游源码镜像**
- amlogic / meson8b（OneCloud）
- bcm53xx（R7000）
- mt7621 / mt7620 / mt7628（JCG Q20 / K2 / 小米 4A）
- ipq40xx（中兴 E2633）
- x86-64（通用）

### **📌 补丁与 DTS 文件**
- 各硬件专用 DTS
- 内核补丁
- OpenWrt target 补丁
- 自定义构建脚本

---

## 🚀 Usage

你可以在自己的 OpenWrt 构建脚本中引用本仓库，例如：

```bash
git clone https://github.com/upleung/openwrt-build-reference.git reference

# 引用 OneCloud amlogic target
rm -rf openwrt/target/linux/amlogic
cp -r reference/onecloud/amlogic-meson8b openwrt/target/linux/amlogic

# 引用 AmlImg 工具
cp reference/common-tools/AmlImg/AmlImg ./AmlImg
chmod +x ./AmlImg
```

---

## 🤝 Contribution

欢迎提交：

- 新硬件资料
- 构建工具
- 补丁
- 上游镜像
- 编译脚本

---

## ⭐ Why This Repository Exists

为了避免：

- 上游仓库被删除  
- 仓库变为私有  
- 构建脚本拉取不到依赖  
- 固件编译失败  
- 多硬件资料分散难以维护  

本仓库将作为 **长期稳定的引用源**，为多硬件 OpenWrt 构建提供可靠支持。


---

## 📁 Repository Structure

目录结构如下：

```
openwrt-build-reference/
│
├── onecloud/                         # 玩客云（Amlogic S805 / Meson8b）专用资料
│   ├── amlogic-meson8b/              # OneCloud 专用 target 源码、补丁
│   ├── uboot/                        # OneCloud 专用 u-boot
│   ├── tools/                        # OneCloud 专用工具（非通用）
│   └── patches/                      # OneCloud 专用补丁
│
├── netgear-r7000/                    # 网件 R7000（BCM53xx）专用资料
│   ├── bcm53xx/                      # R7000 target 源码、补丁
│   ├── patches/                      # R7000 专用补丁
│   └── toolchain/                    # R7000 编译工具链
│
├── jcg-q20/                          # JCG Q20（MT7621）专用资料
│   ├── mt7621/                       # MT7621 target 源码
│   ├── dts/                          # Q20 专用 DTS
│   └── patches/                      # Q20 专用补丁
│
├── xiaomi-4a/                        # 小米路由器 4A（MT7628）专用资料
│   ├── mt7628/                       # MT7628 target 源码
│   ├── uboot/                        # 4A 专用 u-boot
│   └── patches/                      # 4A 专用补丁
│
├── phicomm-k2/                       # 斐讯 K2（MT7620）专用资料
│   ├── mt7620/                       # MT7620 target 源码
│   └── patches/                      # K2 专用补丁
│
├── zte-e2633/                        # 中兴 E2633（IPQ40xx）专用资料
│   ├── ipq40xx/                      # IPQ40xx target 源码
│   └── patches/                      # E2633 专用补丁
│
├── x86-64/                           # X86-64 通用资料
│   ├── configs/                      # X86 构建配置
│   └── tools/                        # X86 构建工具
│
├── common-tools/                     # 所有设备共享的通用工具库（重点）
│   ├── AmlImg/                       # Amlogic 烧录工具（通用）
│   ├── uboot/                        # 通用 u-boot 工具
│   ├── sdk/                          # 通用 SDK
│   ├── build-deps/                   # 通用构建依赖
│   └── scripts/                      # 通用构建脚本
│
└── README.md                         # 仓库说明文档

```

---

## 📄 License
本仓库采用 MIT License，允许自由使用、修改与分发。
