---
title: /QIntel-jcc-erratum
description: Popisuje možnost Microsoft C/C++ COMPILER (MSVC)/QIntel-JCC-erratum.
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520877"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

Možnost **/QIntel-JCC-erratum** je k dispozici v aplikaci Visual Studio 2019 verze 16,5 a novější.

::: moniker-end

::: moniker range=">=vs-2019"

Určuje, že kompilátor vygeneruje pokyny ke zmírnění dopadu na výkon způsobený JCC (kontrola) s aktualizací vyžádal povolení mikrokódu v některých procesorech od společnosti Intel.

## <a name="syntax"></a>Syntaxe

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>Poznámky

V části **/QIntel-JCC-erratum**kompilátor detekuje odkazy a pokyny pro skoky v makrech, které jsou na hranici 32 bajtů. Tyto pokyny zarovnává na hranici. Tato změna snižuje dopad na výkon aktualizací vyžádal povolení mikrokódu, které brání JCC kontrola v některých procesorech Intel. Další informace o kontrola najdete v tématu [zmírňující rizika pro skok podmíněného kódu kontrola](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf) na webu Intel.

Možnost **/QIntel-JCC-erratum** je k dispozici v aplikaci Visual Studio 2019 verze 16,5 a novější. Tato možnost je k dispozici pouze v kompilátorech cílících na x86 a x64. Možnost není k dispozici v kompilátorech, které cílí na procesory ARM.

Možnost **/QIntel-JCC-erratum** je ve výchozím nastavení vypnutá a funguje pouze v optimalizovaných sestaveních. Tato možnost může zvětšit velikost kódu.

**/QIntel-JCC-erratum** je nekompatibilní s [/CLR](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **generování kódu** **C++ jazyka C/** >.

1. Vyberte hodnotu pro vlastnost **Enable Intel JCC kontrola zmírňing** . Kliknutím na **tlačítko OK** aplikujte změnu.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[/Q možnosti (operace nízké úrovně)](q-options-low-level-operations.md)\
\ [možností kompilátoru MSVC](compiler-options.md)
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)

::: moniker-end
