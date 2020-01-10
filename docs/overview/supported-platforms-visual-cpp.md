---
title: Podporované platformy (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 049b28d23c7f5f5f023f3b2964577b75992c2998
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793827"
---
# <a name="supported-platforms-visual-c"></a>Podporované platformy (Visual C++)

Aplikace vytvořené pomocí sady Visual Studio můžou být cílené na různé platformy, a to následujícím způsobem.

|Operační systém|x86|x64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
|Windows Vista|X|X|||
|Windows Server 2008|X|X|||
|Windows 7|X|X|||
|Windows Server 2012 R2|X|X|||
|Windows 8|X|X|X||
|Windows 8.1|X|X|X||
|Windows 10|X|X|X|X|
|Android \*\*|X|X|X|X|
|iOS \*\*|X|X|X|X|
|Linux \*\*\*|X|X|X|X|

\* můžete použít sadu nástrojů platformy Windows XP, která je součástí sady Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012 Update 1 pro sestavování projektů Windows XP a Windows Server 2003. Informace o tom, jak používat tuto sadu nástrojů platformy, najdete v tématu [Konfigurace programů pro systém Windows XP](../build/configuring-programs-for-windows-xp.md). Další informace o změně sady nástrojů platformy naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* můžete nainstalovat vývoj pro **mobilní zařízení pomocí C++**  úlohy v instalačním programu pro Visual Studio 2017 a novějším. V instalačním programu sady Visual Studio 2015 vyberte **volitelný C++ vizuál pro vývoj mobilních aplikací pro různé platformy** a nastavte platformy iOS nebo Android. Pokyny najdete v tématu [instalace vizuálu C++ pro vývoj mobilních aplikací pro různé platformy](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Pokud chcete sestavit kód pro iOS, musíte mít počítač Mac a splňovat jiné požadavky. Seznam požadavků a pokyny k instalaci najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Můžete sestavit kód x86 nebo ARM, který bude odpovídat cílovému hardwaru. Použijte konfigurace x86 k sestavení simulátoru iOS, Microsoft Visual Studio Emulator for Android a některých zařízení s Androidem. Pomocí konfigurací ARM Sestavujte zařízení s iOS a většinu zařízení s Androidem.

\*\*\* můžete nainstalovat vývoj pro **Linux pomocí C++**  úlohy v instalačním programu sady Visual Studio 2017 a novějším pro cílení na platformy Linux. Pokyny najdete v tématu [stažení, instalace a nastavení úlohy pro Linux](../linux/download-install-and-setup-the-linux-development-workload.md). Tato sada nástrojů zkompiluje spustitelný soubor na cílovém počítači, takže můžete sestavit pro libovolnou podporovanou architekturu.

\*\*\*\* podpora ARM64 je k dispozici v aplikaci Visual Studio 2017 nebo novější.

Informace o tom, jak nastavit konfiguraci cílové platformy, najdete v tématu [Postupy: Konfigurace vizuálních C++ projektů pro cílení na 64 platforem x64](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Viz také:

- [Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Začínáme](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
