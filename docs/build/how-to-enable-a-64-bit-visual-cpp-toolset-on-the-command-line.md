---
title: 'Postupy: povolení 64 sady nástrojů MSVC v příkazovém řádku'
ms.date: 07/24/2019
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
ms.openlocfilehash: 60399994cd5fc2f39efeadc6ffcf917138aada37
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078532"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Postupy: povolení MSVC sady nástrojů hostovaného pro x64 v příkazovém řádku (64)

Visual Studio obsahuje kompilátory C++, poskytovatele a další nástroje, které můžete použít k vytvoření verzí aplikací specifických pro platformu, které mohou běžet v systémech Windows s 32, 64 nebo na bázi ARM. Jiné volitelné úlohy sady Visual Studio umožňují používat nástroje C++ pro cílení na jiné platformy, jako je iOS, Android a Linux. Výchozí architektura sestavení používá pro se32 stavování nativního kódu systému Windows pro systém x86 rozhraní 32, které jsou hostovány x86. Máte ale pravděpodobně 64 počítač. Pokud je aplikace Visual Studio nainstalována na 64. operační systém Windows, jsou k dispozici další zástupci příkazového řádku pro vývojáře pro 64 nativní a křížové kompilátory hostované v x64. Při vytváření kódu pro procesory x86, x64 nebo ARM můžete využít výhod procesoru a paměťového prostoru dostupného pro 64 bitový kód pomocí 64 sady nástrojů hostované pro platformu x64.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Použijte zástupce hostovaného příkazového řádku pro vývojáře, který je 64.

Chcete-li získat přístup k těmto příkazům ve Windows 10, otevřete v nabídce **Start** složku pro vaši verzi sady Visual Studio, například sadu **Visual Studio 2019**, a pak zvolte jednu z nativních příkazů pro vývojáře x64 nebo více nástrojů.

![x64 Native Tools Command Prompt](media/x64-native-tools-command-prompt.png "Nativní nástroje x64 v nabídce Start")

Chcete-li získat přístup k těmto příkazům v systému Windows 8, otevřete na obrazovce **Start** **všechny aplikace**. V nadpisu pro nainstalovanou verzi sady Visual Studio otevřete složku sady **Visual Studio** (ve starších verzích sady Visual Studio, může se jednat o název **Visual Studio Tools**). V dřívějších verzích systému Windows klikněte na tlačítko **Start**, rozbalte položku **všechny programy**, složku pro vaši verzi sady **Visual Studio** (a ve starších verzích sady Visual Studio **Visual Studio Tools**). Další informace najdete v tématu [zástupce příkazového řádku pro vývojáře](building-on-the-command-line.md#developer_command_prompt_shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Použití vcvarsall. bat k nastavení architektury hostovaného sestavení s 64

Všechny konfigurace buildu nativního nebo nástroje pro více kompilátorů se dají použít na příkazovém řádku spuštěním souboru příkazu vcvarsall. bat. Tento soubor příkazů konfiguruje cestu a proměnné prostředí, které povolují konkrétní architekturu sestavení v existujícím okně příkazového řádku. Konkrétní pokyny najdete v tématu [umístění souborů příkazů pro vývojáře](building-on-the-command-line.md#developer_command_file_locations).

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Informace o konkrétních nástrojích, které jsou součástí každé edice sady Visual Studio, naleznete v tématu [Visual C++ nástrojů a funkcí v edicích sady Visual Studio](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Informace o použití integrovaného vývojového prostředí (IDE) sady Visual Studio k vytváření 64 aplikací naleznete v tématu [How to: configure Visual C++ Projects to targeting 64-bit Platforms x64](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Když nainstalujete úlohu C++ v instalačním programu sady Visual Studio, vždy nainstaluje 32 – x86, nativní a průřezové nástroje pro sestavení kódu x86 a x64. Pokud zahrnete úlohu Univerzální platforma Windows, nainstaluje také nástroj pro křížové kompilátory hostované v x86 k sestavení kódu ARM. Pokud tyto úlohy nainstalujete na 64 procesor x64, získáte také 64 nativní a nástroje pro křížové kompilátory k sestavení kódu x86, x64 a ARM. 32 bitové a 64 nástroje generují stejný kód, ale 64-bit nástroje podporují více paměti pro předkompilované symboly hlaviček a možnosti pro celou optimalizaci programu ([/GL](reference/gl-whole-program-optimization.md) a [/LTCG](reference/ltcg-link-time-code-generation.md)). Pokud při používání 32 bitových nástrojů spustíte limity paměti, vyzkoušejte nástroje na 64.

## <a name="see-also"></a>Viz také

[Konfigurace projektů C++ pro 64 cíle platformy x64](configuring-programs-for-64-bit-visual-cpp.md)<br/>
