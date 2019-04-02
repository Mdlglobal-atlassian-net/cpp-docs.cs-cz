---
title: 'Postupy: Povolení 64bitovým kompilátorem MSVC sady nástrojů příkazového řádku'
ms.date: 03/29/2018
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: 8436254a3d8c5c1dae018c2309ceaad7bd5b2408
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769274"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Postupy: Povolit 64-Bit, x64 hostované MSVC sady nástrojů v příkazovém řádku

Visual Studio obsahuje kompilátory C++, linkers a dalších nástrojů, které vám umožní vytvářet specifické pro platformu verze aplikací, které poběží v operačních systémech Windows 32bitové, 64bitové nebo založené na ARM. Další volitelné úlohy sady Visual Studio umožňují použijte nástroje C++ k cílení na jiných platformách, jako je iOS, Androidu a Linuxu. Výchozí architektura sestavení používá 32bitové, hostované x86 nástroje k vytvoření 32-bit, x86 nativní kód Windows. Ale pravděpodobně máte 64bitový počítač. Můžete využít výhod procesoru a paměti k dispozici pro 64bitový kód pomocí nástrojů 64-bit, hostované x64 při sestavování kódu pro x86, x64 nebo procesory ARM.

> [!NOTE]
> Informace o konkrétních nástrojích, které jsou součástí každé edici sady Visual Studio najdete v tématu [nástrojů Visual C++ a funkcí v edicích nástroje Visual Studio](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Informace o tom, jak použít rozhraní IDE sady Visual Studio k vytvoření 64bitových aplikací naleznete v tématu [jak: Konfigurace projektů Visual C++ pro cílení 64-Bit, x64 platformy](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Když nainstalujete sadu funkcí jazyka C++ v instalačním programu sady Visual Studio, vždy nainstaluje 32bitové, hostované x86, nativní a multiplatformní kompilátoru nástroje potřebné k vytváření x86 a x64 kódu. Pokud zahrnete úlohu univerzální platformy Windows, nainstaluje taky hostované x86 křížovým kompilátorem nástroje potřebné k vytváření kódu ARM. Pokud nainstalujete tyto úlohy na 64-bit, x64 procesoru, můžete také získat 64bitové nativní a křížový kompilátor nástroje pro vytváření x86, x 64 a ARM kódu. 32bitová verze a 64bitová verze nástrojů generují stejný kód, ale 64bitové nástroje podporují více paměti pro předkompilované symboly a optimalizace celého programu ([/GL](reference/gl-whole-program-optimization.md) a [parametru/LTCG](reference/ltcg-link-time-code-generation.md)) možnosti. Pokud narazíte na limity paměti při použití nástroje 32-bit, zkuste 64bitových nástrojů.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Použít zástupce příkazového řádku prostředí pro vývojáře 64-bit

Při instalaci systému Visual Studio v operačním systému Windows 64-bit, nejsou k dispozici další vývojářské příkazového řádku zkratky pro 64-bit, hostované x64 nativní a křížové kompilátory. Pro přístup k těmto příkazového řádku ve Windows 10 na **Start** nabídky, otevřete složku pro vaši verzi sady Visual Studio, třeba **Visual Studio 2017**a pak vyberte jednu z x64 nativních nebo křížových nástrojů příkazový řádek pro vývojáře. Pro přístup k těmto příkazové řádky v systému Windows 8 na **Start** obrazovce otevřete **všechny aplikace**. V části pro nainstalovanou verzi sady Visual Studio, otevřete **sady Visual Studio** složku (ve starších verzích sady Visual Studio, může mít název **Visual Studio Tools**). Ve starších verzích Windows, zvolte **Start**, rozbalte **všechny programy**, složku pro vaši verzi **sady Visual Studio** (a ke starším verzím sady Visual Studio,  **Nástroje sady Visual Studio**). Další informace najdete v tématu [zkratky příkazového řádku pro vývojáře](building-on-the-command-line.md#developer_command_prompt_shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Nastavení architektury 64-bit hostovaného sestavení pomocí Vcvarsall.bat

Všechny nativní nebo nástrojů kompilátoru můžou být použité konfigurace sestavení na příkazovém řádku spuštěním vcvarsall.bat pro různé soubor příkazů. Soubor tento příkaz nastaví cesty a proměnných prostředí, které umožňují konkrétní sestavení architektury ve stávajícím okně příkazového řádku. Konkrétní pokyny najdete v tématu [umístění souborů pro vývojáře příkaz](building-on-the-command-line.md#developer_command_file_locations).

## <a name="see-also"></a>Viz také:

[Konfigurace projektů C++ pro 64bitové, x64 cíle](configuring-programs-for-64-bit-visual-cpp.md)<br/>
