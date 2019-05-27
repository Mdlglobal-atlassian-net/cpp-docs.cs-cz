---
title: Podporované platformy (Visual C++)
ms.date: 05/14/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 950f62b4cbf1255af97f1f4950bab03c58c2ceba
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174856"
---
# <a name="supported-platforms-visual-c"></a>Podporované platformy (Visual C++)

Aplikace vytvořené pomocí sady Visual Studio můžete zacílit na různé platformy následujícím způsobem.

|Operační systém|x86|x64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|X\*|X\*|||
|Windows Server 2003|X\*|X\*|||
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

\* Můžete použít sadu nástrojů platformy Windows XP zahrnuty v sadě Visual Studio 2017, Visual Studio 2015, Visual Studio 2013 a Visual Studio 2012 Update 1 nebo novějším k sestavení projektů Windows XP a Windows Server 2003. Informace o tom, jak použít tuto sadu nástrojů platformy najdete v tématu [konfigurace aplikací pro Windows XP](../build/configuring-programs-for-windows-xp.md). Další informace o změně sada nástrojů platformy najdete v tématu [jak: Změna cílové architektury a sady nástrojů](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\* Můžete nainstalovat **vývoj mobilních aplikací pomocí C++**  úloh v instalačním programu pro Visual Studio 2017 a novější. V instalačním programu sady Visual Studio 2015, zvolte nepovinné **Visual C++ pro vývoj pro různé platformy mobilních aplikací** komponentu do cílové platformu iOS nebo Android. Pokyny najdete v tématu [instalaci Visual C++ pro vývoj mobilních řešení napříč platformami](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). K vytváření kódu s Iosem, musíte mít počítači Mac a splňovat další požadavky. Seznam požadavků a pokyny k instalaci najdete v tématu [instalace a konfigurace nástrojů pro vytváření pomocí iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Můžete vytvořit x86 nebo ARM kód tak, aby odpovídaly cílové hardwaru. Použití x86 konfigurací pro sestavení pro některá zařízení s Androidem, simulátoru iOS a Microsoft Visual Studio Emulator for Android. Konfigurace ARM použijte k sestavování pro zařízení s Iosem a většiny zařízení s Androidem.

\*\*\* Můžete nainstalovat **vývoj pro Linux v C++**  úloh v instalačním programu pro Visual Studio 2017 a novějším na cílové platformy Linux. Pokyny najdete v tématu [stažení, instalace a nastavení úloh Linux](../linux/download-install-and-setup-the-linux-development-workload.md). Tato sada nástrojů zkompiluje spustitelný soubor na cílovém počítači, abyste mohli sestavit pro jakékoliv podporované architektuře.

\*\*\*\* Podpora ARM64 je k dispozici v sadě Visual Studio 2017 nebo novější.

Informace o tom, jak nastavit konfiguraci cílové platformy naleznete v tématu [jak: Konfigurace projektů Visual C++ pro cílení 64-Bit, x64 platformy](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Viz také:

- [Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Začínáme](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
