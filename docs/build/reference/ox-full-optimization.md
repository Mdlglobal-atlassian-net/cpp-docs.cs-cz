---
title: -Ox (povolení většiny optimalizací pro rychlost) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1da84c3a4ec481d3af2880a80f5923bf0c50cc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438077"
---
# <a name="ox-enable-most-speed-optimizations"></a>/OX (povolení většiny optimalizací pro rychlost)

**/Ox** – možnost kompilátoru umožňuje kombinace optimalizací, které upřednostnit rychlost. V některých verzích sady Visual Studio IDE a zprávu nápovědy kompilátoru, tento postup se nazývá *úplná optimalizace*, ale **/Ox** umožňuje pouze podmnožinu zajišťuje možnosti optimalizace rychlost – možnost kompilátoru **/O2**.

## <a name="syntax"></a>Syntaxe

> /OX

## <a name="remarks"></a>Poznámky

**/Ox** umožňuje – možnost kompilátoru **/O** upřednostnit rychlost možností kompilátoru. **/Ox** – možnost kompilátoru neobsahuje další [/GF (odstranění duplicitní řetězce)](../../build/reference/gf-eliminate-duplicate-strings.md) a [/Gy (povolení funkce propojení na úrovni)](../../build/reference/gy-enable-function-level-linking.md) možnosti umožněné [/O1 nebo/O2 (minimální velikost, maximální rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Další možnosti použil(a) **/O1** a **/O2** může způsobit, že ukazatele na řetězce nebo k funkcím sdílet cílovou adresu, která může mít vliv na ladění a striktní jazykem. **/Ox** možnost je snadný způsob, jak povolení většiny optimalizací pro bez zahrnutí **/GF** a **/Gy**. Další informace najdete v tématu popisy [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) a [/Gy](../../build/reference/gy-enable-function-level-linking.md) možnosti.

**/Ox** – možnost kompilátoru je stejné jako v kombinaci s použitím následujících možností:

- [/Ob (rozbalení vložené funkce)](../../build/reference/ob-inline-function-expansion.md), kde je parametr možnosti 2 (**/ob2**)

- [/Og (globální optimalizace)](../../build/reference/og-global-optimizations.md)

- [/Oi (generování vnitřních funkcí)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (upřednostnit rychlý kód)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (vynechání ukazatele na rámec)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** se vzájemně vylučuje od:

- [/ O1 (pro minimalizaci velikosti)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (maximální rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (zakázání (ladění))](../../build/reference/od-disable-debug.md)

Můžete je zrušit Posun směrem k rychlosti **/Ox** – možnost kompilátoru při zadání **/Oxs**, které kombinuje **/Ox** – možnost kompilátoru s  [ /OS (upřednostnit malý Kód)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Kombinované možnosti upřednostnit menší velikost kódu.

Použít všechny dostupné souboru úroveň optimalizace pro buildy vydaných verzí, doporučujeme vám určit [/O2 (maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) místo **/Ox**, a [/O1 (minimalizaci velikosti)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) místo z **/Oxs**. Pro ještě více optimalizace ve verzi sestavení, zvažte také [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru a [parametru/LTCG (generování kódu při propojování odkaz)](../../build/reference/ltcg-link-time-code-generation.md) – možnost linkeru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, otevřete **C/C++** a klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také

[/O – možnosti (optimalizace kódu)](../../build/reference/o-options-optimize-code.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)