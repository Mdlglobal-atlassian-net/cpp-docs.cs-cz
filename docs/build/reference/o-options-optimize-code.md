---
title: /O možnosti (optimalizace kódu)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: ffd3023120f1d930a24ccef6fa297594062322df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320419"
---
# <a name="o-options-optimize-code"></a>/O možnosti (optimalizace kódu)

**/O** možnosti řízení různých optimalizací, které vám pomůžou vytvořit kód pro maximální rychlost a minimální velikosti.

- [/ O1](o1-o2-minimize-size-maximize-speed.md) nastaví kombinace optimalizací, které generují kód minimální velikost.

- [/ O2](o1-o2-minimize-size-maximize-speed.md) nastaví kombinace optimalizací, který optimalizuje kód pro maximální rychlost.

- [/Ob](ob-inline-function-expansion.md) řídí rozbalení vložených funkcí.

- [/Od](od-disable-debug.md) zakáže optimalizaci pro rychlost kompilace a zjednodušení ladění.

- [/Og](og-global-optimizations.md) povolí globální optimalizace.

- [/OI](oi-generate-intrinsic-functions.md) vytváří vnitřní funkce pro odpovídající funkce volání.

- [/OS](os-ot-favor-small-code-favor-fast-code.md) instruuje kompilátor, aby optimalizace pro velikost upřednostnil před optimalizací pro rychlost.

- [/Ot](os-ot-favor-small-code-favor-fast-code.md) (výchozí nastavení) instruuje kompilátor, aby optimalizací pro rychlost upřednostnil před Optimalizace velikosti.

- [/Ox](ox-full-optimization.md) je kombinace možností, který vybere několik optimalizací s důrazem na rychlost. Je striktní podmnožinou **/O2** optimalizace.

- [/Oy](oy-frame-pointer-omission.md) potlačí vytváření ukazatelů rámců v zásobníku volání pro rychlejší volání funkce.

## <a name="remarks"></a>Poznámky

Můžete zkombinovat více **/O** možnosti do příkazu jednu možnost. Například **/Odi** je stejný jako **/Od /Oi**. Některé možnosti se vzájemně vylučují a způsobí chybu kompilátoru, je-li použít společně. Zobrazit jednotlivé **/O** možnosti pro další informace.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
