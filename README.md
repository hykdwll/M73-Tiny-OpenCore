<div align="center">
  
  # **适用于联想 ThinkCentre M73 Tiny 的 OpenCore 0.8.9**
  
  [![OpenCore 0.8.9](https://img.shields.io/badge/OpenCore-0.8.9-004852)](https://github.com/acidanthera/OpenCorePkg)
  [![macOS Catalina 10.15 至 Ventura 13.2](https://img.shields.io/badge/macOS-Catalina%2010.15%20至%20Ventura%2013.2-67320A?logo=apple)](https://apple.com/macos/ventura)
  [![是否维护？是！](https://img.shields.io/badge/是否维护%3F-是！-334512.svg)](https://github.com/UHDbits/M73-Tiny-OpenCore/graphs/commit-activity)

  [![下载](https://img.shields.io/badge/下载-114B14?logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij48cGF0aCBkPSJNNC45NyAxMS4wM2EuNzUuNzUgMCAxIDEgMS4wNi0xLjA2TDExIDE0Ljk0VjIuNzVhLjc1Ljc1IDAgMCAxIDEuNSAwdjEyLjE5bDQuOTctNC45N2EuNzUuNzUgMCAxIDEgMS4wNiAxLjA2bC02LjI1IDYuMjVhLjc1Ljc1IDAgMCAxLTEuMDYgMGwtNi4yNS02LjI1Wm0tLjIyIDkuNDdhLjc1Ljc1IDAgMCAwIDAgMS41aDE0LjVhLjc1Ljc1IDAgMCAwIDAtMS41SDQuNzVaIiBzdHlsZT0iZmlsbDojZmZmZmZmIj48L3BhdGg+PC9zdmc+)](https://github.com/UHDbits/M73-Tiny-OpenCore/releases/latest)
  [![旧版 Mac OS X/macOS 配置在此处](https://img.shields.io/badge/点击此处获取旧版%20Mac%20OS%20X%2FmacOS%20支持-792316)](https://github.com/UHDbits/M73-Tiny-OpenCore/tree/legacy)

  <img src="https://github.com/UHDbits/M73-Tiny-OpenCore/raw/main/Resources/Images/ThinkCentre.png" alt="ThinkCentre M73 Tiny" width="400px"/>
  
  | ![Catalina 关于本机（深色模式）](/Resources/Images/About%20This%20Mac/DarkCatalinaAboutThisMac.png#gh-dark-mode-only) ![Catalina 关于本机（浅色模式）](/Resources/Images/About%20This%20Mac/LightCatalinaAboutThisMac.png#gh-light-mode-only) | ![Ventura 关于本机（深色模式）](/Resources/Images/About%20This%20Mac/DarkVenturaAboutThisMac.png#gh-dark-mode-only) ![Ventura 关于本机（浅色模式）](/Resources/Images/About%20This%20Mac/LightVenturaAboutThisMac.png#gh-light-mode-only) |
  | ----------------------------------------- | ----------------------------------------- |
  
  ## ⚠️ 警告 ⚠️
  
  **不建议使用预构建的 OpenCore 配置。它们可能不适用于您计算机的确切硬件，可能启用了您不需要的功能，可能已过时，并且更难诊断问题。此配置旨在作为帮助您为这款 ThinkCentre 创建自己的 OpenCore 配置的指南，但您也可以按原样使用，风险自负。**
  
  ## 目录
  
  [**系统规格**](#系统规格)
  
  [**操作步骤**](#操作步骤)

  [**更新 OpenCore/macOS**](#更新-opencoremacos)

  [**已知问题**](#已知问题)
  
  ## 系统规格
  
  | 组件 | 型号 |
  | :-: | :-: |
  | 处理器 | Intel Core i7-4785T（4核8线程）@ 2.20GHz |
  | 内存 | 2x8GB（16GB）DDR3-1600 |
  | 显卡 | Intel HD Graphics 4600 |
  | 存储 | 三星 870 EVO 1TB SSD |
  | 音频 | Realtek ALC283（存在已知问题） |
  | 内置无线网卡/蓝牙 | Intel Centrino Wireless-N 7260（无法工作） |
  | USB 无线网卡 | TP-Link Archer T3U（驱动未包含，可在[此处](https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter)找到） |
  | 以太网 | Intel I217-V |
  
  **如果您的系统与这些规格不匹配（除了不重要的部分，如无线网卡），则不能保证此配置适用于您。如果您无法使其工作，可以创建一个 issue，我将尽力帮助您。**

  ## 操作步骤
  
  **通过访问链接并按照列出的指示完成以下步骤。如果某一步骤标有 &#42;，表示它是可选的，但强烈推荐。如果某一步骤标有 &#42;&#42;，表示它是可选的且不是必需的。**

  | 步骤编号 | 链接/操作说明 |
  | :-: | :-: |
  | 0.5 | [对于 ThinkCentre M93p 用户，请使用此工具在 Windows 上映射您的 USB 端口。确保在设置中启用“使用原生类”，并使用“iMac18,1”作为型号标识符。](https://github.com/USBToolBox/tool)
  | 1 | [创建 USB 安装盘（不要移动 EFI 文件夹。不需要 ProperTree。）](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/#making-the-installer) |
  | 2 | 将此仓库中的“EFI”文件夹移动到 macOS 上的 EFI 分区、Windows 上的 USB 驱动器根目录或 Linux 上的“OPENCORE”分区。确保移动整个文件夹本身，而不仅仅是其中的文件。
  | 3 | [根据本文档修改您的 BIOS 设置。如果在 BIOS 中没有看到“VT-d”，可以跳过。](/Resources/Documentation/BIOSSettings.md)
  | 4 | [安装过程（跳过“仔细检查您的工作”。如果您想多系统启动，可以查看“OpenCore 多系统启动指南”。）](https://dortania.github.io/OpenCore-Install-Guide/installation/installation-process.html#booting-the-opencore-usb)
  | 5 | **（仅适用于 Ventura）** [使用 OpenCore Legacy Patcher 获取图形加速。](/Resources/Documentation/VenturaOCLP.md)
  | 6* | [将 OpenCore 从 USB 移动到 macOS 驱动器（跳过底部的“Legacy”部分）](https://dortania.github.io/OpenCore-Post-Install/universal/oc2hdd.html)
  | 7* | [使用 OpenCore 修复 iMessage 和其他服务（即使您不使用 iServices，也强烈推荐这样做，因为否则您将拥有一个通用序列号，这不是一个好主意。）](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html)
  | 8** | **（Monterey 及更低版本）** [修改 OpenCore 配置以提高安全性。](/Resources/Documentation/Security.md)

  ## 更新 OpenCore/macOS
  
  ### 使用此配置的新版本更新 OpenCore
  **如果您想使用此配置的新版本更新 OpenCore，只需下载新的 EFI 文件夹，挂载 EFI 分区，并将文件夹复制到该分区。请注意，如果您对配置进行了任何更改，请确保记住它们或将它们保存在某个地方，因为所做的任何更改都将被覆盖。**

  ### 手动更新 OpenCore/macOS
  **如果您想手动更新 OpenCore，可以遵循[本指南](https://dortania.github.io/OpenCore-Post-Install/universal/update.html#updating-opencore)（较难遵循，但推荐，并且会告诉您如何更新 macOS），或者遵循[本指南](https://www.insanelymac.com/forum/topic/347035-guide-updating-and-maintaining-opencore-new-method/)（较容易遵循，但不推荐）。如果您想更新 macOS 13 Ventura，请遵循[此处的指南](/Resources/Documentation/VenturaOCLP.md#before-updating-macos)。**

  ## 已知问题
  
  ### OpenCore Legacy Patcher 问题
  **由于 macOS 13 Ventura 不官方支持这款 ThinkCentre 中的硬件，我们必须使用一个名为“OpenCore Legacy Patcher”的工具来应用补丁，使我们能够正常使用 Ventura。遗憾的是，这些补丁确实有一些小问题。要查看影响这款 ThinkCentre 的问题，请查看[此链接](https://github.com/dortania/OpenCore-Legacy-Patcher/issues/1008/)并在“已知问题”中查找“Haswell”。如前所述，这些错误相当轻微，不会影响大多数人。**

  ### 无 VGA 输出
  **由于 macOS 不官方支持 VGA，您将无法通过 ThinkCentre 上的 VGA 端口输出 macOS 用户界面。目前，这一点无法修复。**

  ### HD4400 在 Monterey 12.3+ 安装过程中崩溃
  **对于 HD4400，Monterey 12.3 或更高版本在安装的“迁移助理”部分会崩溃。有时，您可以通过该屏幕，但之后会冻结。这个问题只能通过将您的 CPU 升级到带有 HD4600 核显的 CPU 来解决。目前尚不清楚在 Ventura 中是否会发生这种情况。**

  ### HD4400 出现闪烁和冻结
  **HD4400 在 macOS 中有许多问题。例如，一些图标可能会丢失（下图），可能会发生一些随机冻结，图标可能会被替换，甚至可能有更多问题。在较新版本的 macOS 中，这可能会使系统几乎无法使用。目前这一点无法修复，您唯一能做的就是将您的 CPU 升级到带有 HD4600 核显的 CPU。**

  ![图标丢失示例（深色模式）](/Resources/Images/Missing%20Icons/DarkMissingIcons.png#gh-dark-mode-only) ![图标丢失示例（浅色模式）](/Resources/Images/Missing%20Icons/LightMissingIcons.png#gh-light-mode-only)

  ### 无麦克风插孔输入
  **开箱即用，此配置没有麦克风插孔输入。通过使用[本指南](https://dortania.github.io/OpenCore-Post-Install/universal/audio.html#making-layout-id-more-permanent)将 AppleALC 布局 ID 更改为 66，可以获得麦克风插孔输入，但这会导致耳机音频失真。这可以通过进入系统偏好设置 -> 声音，并将“平衡”滑块向左或向右移动来修复。由于耳机音频失真，此配置开箱即用时未设置为支持麦克风插孔输入。组合插孔（标记为耳机插孔）不受此问题影响，开箱即可正常工作。**
  
  ![将“平衡”滑块向左或向右移动（深色模式）](/Resources/Images/Headphones%20Fix/DarkHeadphonesFix.png#gh-dark-mode-only) ![将“平衡”滑块向左或向右移动（浅色模式）](/Resources/Images/Headphones%20Fix/LightHeadphonesFix.png#gh-light-mode-only)
  
  [**跳至顶部**](#适用于联想-thinkcentre-m73-tiny-的-opencore-089)

</div>
