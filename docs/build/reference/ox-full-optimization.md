---
title: -Ox (Povolit většinu optimalizace rychlost) | Microsoft Docs
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
ms.openlocfilehash: 569563bff030904988e93db749438eaeb58ce9db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378379"
---
# <a name="ox-enable-most-speed-optimizations"></a>/OX (Povolit většinu rychlost optimalizace)

**/Ox** – možnost kompilátoru umožňuje kombinaci optimalizace, které upřednostnit rychlost. Některé verze Visual Studio IDE a zprávy nápovědy kompilátoru tomu se říká *úplná optimalizace*, ale **/Ox** umožňuje pouze podmnožinu ve povolené možnosti optimalizace rychlost – možnost kompilátoru **/O2**.

## <a name="syntax"></a>Syntaxe

> /OX

## <a name="remarks"></a>Poznámky

**/Ox** umožňuje – možnost kompilátoru **/O** kompilátoru možnosti upřednostnit rychlosti. **/Ox** – možnost kompilátoru nezahrnuje další [/GF (odstranění duplicitních řetězců)](../../build/reference/gf-eliminate-duplicate-strings.md) a [/Gy (povolení propojení na úrovni funkcí)](../../build/reference/gy-enable-function-level-linking.md) ve povolenémožnosti[/O1 nebo/O2 (minimální velikost, maximální rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Další možnosti použít tak **/O1** a **/O2** může způsobit ukazatele na řetězce a funkce sdílet cílová adresa, která může ovlivnit ladění a striktní jazyk shoda. **/Ox** možnost je snadný způsob, jak povolit většinu optimalizace bez včetně **/GF** a **/Gy**. Další informace najdete v tématu popisy [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) a [/Gy](../../build/reference/gy-enable-function-level-linking.md) možnosti.

**/Ox** – možnost kompilátoru je stejný jako v kombinaci pomocí následujících možností:

- [/Ob (rozbalení vložené funkce)](../../build/reference/ob-inline-function-expansion.md), kde parametr option je 2 (**/Ob2**)

- [/Og (globální optimalizace)](../../build/reference/og-global-optimizations.md)

- [/Oi (generování vnitřních funkcí)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (upřednostnit rychlý kód)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (vynechání ukazatele)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** se vzájemně vylučují z:

- [/ O1 (minimální velikost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (maximální rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (zakázání (ladění))](../../build/reference/od-disable-debug.md)

Posun směrem k rychlosti můžete zrušit **/Ox** – možnost kompilátoru zadáte-li **/Oxs**, které kombinuje **/Ox** – možnost kompilátoru s [/Os (upřednostnit malý Kód)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Kombinovaná možnosti upřednostnit menší velikost kódu.

Pokud chcete nainstalovat všechny dostupné Optimalizace souborů pro sestavení pro vydání, doporučujeme zadáte [/O2 (maximalizovat rychlost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) místo **/Ox**, a [/O1 (minimalizovat velikost)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) místo z **/Oxs**. Pro i další optimalizace ve verzi sestavení, zvažte také [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md) – možnost kompilátoru a [/ltgc (vytváření kódu v době propojování)](../../build/reference/ltcg-link-time-code-generation.md) – možnost linkeru.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V části **vlastnosti konfigurace**, otevřete **C/C++** a potom zvolte **optimalizace** stránku vlastností.

1. Změnit **optimalizace** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Viz také

[/O – možnosti (optimalizace kódu)](../../build/reference/o-options-optimize-code.md)  
[Možnosti kompilátoru](../../build/reference/compiler-options.md)  
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)