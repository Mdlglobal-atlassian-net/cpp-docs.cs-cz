---
title: /OX (povolení většiny optimalizací pro rychlost)
ms.date: 10/18/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: e39905608087425fe5a445f4ef88434d73bb2ded
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811274"
---
# <a name="ox-enable-most-speed-optimizations"></a>/OX (povolení většiny optimalizací pro rychlost)

**/Ox** – možnost kompilátoru umožňuje kombinace optimalizací, které upřednostnit rychlost. V některých verzích sady Visual Studio IDE a zprávu nápovědy kompilátoru, tento postup se nazývá *úplná optimalizace*, ale **/Ox** umožňuje pouze podmnožinu zajišťuje možnosti optimalizace rychlost – možnost kompilátoru **/O2**.

## <a name="syntax"></a>Syntaxe

> **/OX**

## <a name="remarks"></a>Poznámky

**/Ox** umožňuje – možnost kompilátoru **/O** upřednostnit rychlost možností kompilátoru. **/Ox** – možnost kompilátoru neobsahuje další [/GF (odstranění duplicitní řetězce)](gf-eliminate-duplicate-strings.md) a [/Gy (povolení funkce propojení na úrovni)](gy-enable-function-level-linking.md) možnosti umožněné [/O1 nebo/O2 (minimální velikost, maximální rychlost)](o1-o2-minimize-size-maximize-speed.md). Další možnosti použil(a) **/O1** a **/O2** může způsobit, že ukazatele na řetězce nebo k funkcím sdílet cílovou adresu, která může mít vliv na ladění a striktní jazykem. **/Ox** možnost je snadný způsob, jak povolení většiny optimalizací pro bez zahrnutí **/GF** a **/Gy**. Další informace najdete v tématu popisy [/GF](gf-eliminate-duplicate-strings.md) a [/Gy](gy-enable-function-level-linking.md) možnosti.

**/Ox** – možnost kompilátoru je stejné jako v kombinaci s použitím následujících možností:

- [/Ob (rozbalení vložené funkce)](ob-inline-function-expansion.md), kde je parametr možnosti 2 (**/ob2**)

- [/Og (globální optimalizace)](og-global-optimizations.md)

- [/Oi (generování vnitřních funkcí)](oi-generate-intrinsic-functions.md)

- [/Ot (upřednostnit rychlý kód)](os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (vynechání ukazatele na rámec)](oy-frame-pointer-omission.md)

**/Ox** se vzájemně vylučuje od:

- [/ O1 (pro minimalizaci velikosti)](o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (maximální rychlost)](o1-o2-minimize-size-maximize-speed.md)

- [/Od (zakázání (ladění))](od-disable-debug.md)

Můžete je zrušit Posun směrem k rychlosti **/Ox** – možnost kompilátoru při zadání **/Oxs**, které kombinuje **/Ox** – možnost kompilátoru s  [ /OS (upřednostnit malý Kód)](os-ot-favor-small-code-favor-fast-code.md). Kombinované možnosti upřednostnit menší velikost kódu.  **/Oxs** možnost je přesně stejné jako zadání **/Ox** **/Os** při možnosti se zobrazí v tomto pořadí.

Použít všechny dostupné souboru úroveň optimalizace pro buildy vydaných verzí, doporučujeme vám určit [/O2 (maximalizovat rychlost)](o1-o2-minimize-size-maximize-speed.md) místo **/Ox**, a [/O1 (minimalizaci velikosti)](o1-o2-minimize-size-maximize-speed.md) místo z **/Oxs**. Pro ještě více optimalizace ve verzi sestavení, zvažte také [/GL (optimalizace celého programu)](gl-whole-program-optimization.md) – možnost kompilátoru a [parametru/LTCG (generování kódu při propojování odkaz)](ltcg-link-time-code-generation.md) – možnost linkeru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, otevřete **C/C++** a klikněte na tlačítko **optimalizace** stránku vlastností.

1. Upravit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také:

[/O – možnosti (optimalizace kódu)](o-options-optimize-code.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
