---
title: Podporované platformy (Visual C++)
ms.date: 12/02/2019
ms.technology: cpp-tools
helpviewer_keywords:
- Visual C++, platforms supported
- platforms [C++]
ms.assetid: 0d893056-4008-411a-b3d1-5f57fd7da95c
ms.openlocfilehash: 049b28d23c7f5f5f023f3b2964577b75992c2998
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "75793827"
---
# <a name="supported-platforms-visual-c"></a>Podporované platformy (Visual C++)

Aplikace vytvořené pomocí sady Visual Studio lze cílit na různé platformy následujícím způsobem.

|Operační systém|x86|x64|ARM|ARM64\*\*\*\*|
|----------------------|---------|---------|---------|---------|
|Windows XP|×\*|×\*|||
|Windows Server 2003|×\*|×\*|||
|Windows Vista|×|×|||
|Windows Server 2008|×|×|||
|Windows 7|×|×|||
|Windows Server 2012 R2|×|×|||
|Windows 8|×|×|×||
|Windows 8.1|×|×|×||
|Windows 10|×|×|×|×|
|Android\*\*|×|×|×|×|
|Ios\*\*|×|×|×|×|
|Linux\*\*\*|×|×|×|×|

\*Sadu nástrojů platformy Windows XP zahrnutou ve Visual Studiu 2017, Visual Studiu 2015, Visual Studiu 2013 a Visual Studio 2012 Update 1 můžete použít k sestavení projektů windows xp a windows server 2003. Informace o použití této sady nástrojů platformy naleznete v [tématu Configuring Programs for Windows XP](../build/configuring-programs-for-windows-xp.md). Další informace o změně sady nástrojů platformy naleznete v [tématu How to: Modify the Target Framework and Platform Toolset](../build/how-to-modify-the-target-framework-and-platform-toolset.md).

\*\*Vývoj mobile **s úlohami C++** můžete nainstalovat do instalačního programu pro Visual Studio 2017 a novější. V nastavení Visual Studia 2015 zvolte volitelnou komponentu **Visual C++ for Cross Platform Mobile Development,** která se zaměří na platformy iOS nebo Android. Pokyny naleznete v [tématu Instalace visual c++ pro vývoj mobilních zařízení napříč platformami](/visualstudio/cross-platform/install-visual-cpp-for-cross-platform-mobile-development). Chcete-li vytvořit kód iOS, musíte mít počítač Mac a splňovat další požadavky. Seznam předpokladů a pokynů k instalaci najdete v [tématu Instalace a konfigurace nástrojů pro sestavení pomocí iOS](/visualstudio/cross-platform/install-and-configure-tools-to-build-using-ios). Můžete vytvořit kód x86 nebo ARM tak, aby odpovídal cílovému hardwaru. Konfigurace x86 slouží k sestavení simulátoru iOS, emulátoru Microsoft Visual Studia pro Android a některých zařízení se systémem Android. Pomocí konfigurací ARM můžete vytvářet pro zařízení se systémem iOS a většinu zařízení android.

\*\*\*Vývoj Linuxu s úlohami **C++** můžete nainstalovat do instalačního programu pro Visual Studio 2017 a novějšího a cílit na platformy Linuxu. Pokyny naleznete v [tématu Stažení, Instalace a nastavení úlohy Linuxu](../linux/download-install-and-setup-the-linux-development-workload.md). Tato sada nástrojů zkompiluje spustitelný soubor v cílovém počítači, takže můžete vytvářet pro libovolnou podporovanou architekturu.

\*\*\*\*Podpora ARM64 je dostupná ve Visual Studiu 2017 a novějším.

Informace o nastavení konfigurace cílové platformy najdete v [tématu Postup: Konfigurace projektů Visual C++ na cílové 64bitové platformy x64](../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

## <a name="see-also"></a>Viz také

- [Nástroje a funkce Visual C++ v různých edicích sady Visual Studio](visual-cpp-tools-and-features-in-visual-studio-editions.md)
- [Začínáme](/visualstudio/ide/getting-started-with-cpp-in-visual-studio)
