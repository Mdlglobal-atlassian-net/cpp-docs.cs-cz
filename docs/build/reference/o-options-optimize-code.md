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
ms.openlocfilehash: d884da19936949f2feeb96cb1fb88057d5dcd948
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419696"
---
# <a name="o-options-optimize-code"></a>/O možnosti (optimalizace kódu)

**/O** možnosti řízení různých optimalizací, které vám pomůžou vytvořit kód pro maximální rychlost a minimální velikosti.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nastaví kombinace optimalizací, které generují kód minimální velikost.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nastaví kombinace optimalizací, který optimalizuje kód pro maximální rychlost.

- [/Ob](../../build/reference/ob-inline-function-expansion.md) řídí rozbalení vložených funkcí.

- [/Od](../../build/reference/od-disable-debug.md) zakáže optimalizaci pro rychlost kompilace a zjednodušení ladění.

- [/Og](../../build/reference/og-global-optimizations.md) povolí globální optimalizace.

- [/OI](../../build/reference/oi-generate-intrinsic-functions.md) vytváří vnitřní funkce pro odpovídající funkce volání.

- [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) instruuje kompilátor, aby optimalizace pro velikost upřednostnil před optimalizací pro rychlost.

- [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (výchozí nastavení) instruuje kompilátor, aby optimalizací pro rychlost upřednostnil před Optimalizace velikosti.

- [/Ox](../../build/reference/ox-full-optimization.md) je kombinace možností, který vybere několik optimalizací s důrazem na rychlost. Je striktní podmnožinou **/O2** optimalizace.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) potlačí vytváření ukazatelů rámců v zásobníku volání pro rychlejší volání funkce.

## <a name="remarks"></a>Poznámky

Můžete zkombinovat více **/O** možnosti do příkazu jednu možnost. Například **/Odi** je stejný jako **/Od /Oi**. Některé možnosti se vzájemně vylučují a způsobí chybu kompilátoru, je-li použít společně. Zobrazit jednotlivé **/O** možnosti pro další informace.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
