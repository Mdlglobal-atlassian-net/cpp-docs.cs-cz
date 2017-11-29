---
title: "-O možnosti (Optimalizace kódu) | Microsoft Docs"
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
dev_langs: C++
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 58f8aeda2570fef394b5a47d49c5dda090d8e1ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="o-options-optimize-code"></a>/O možnosti (optimalizace kódu)

**/O** možnosti určují různé optimalizace, které vám pomůže vytvořit kód pro maximální rychlost nebo minimální velikost.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nastaví kombinaci optimalizace, které generování kódu minimální velikost.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) nastaví kombinaci optimalizace optimalizuje kód pro maximální rychlost.

- [/Ob](../../build/reference/ob-inline-function-expansion.md) řídí vložené funkce rozšíření.

- [/Od](../../build/reference/od-disable-debug.md) zakáže optimalizace pro urychlení kompilace a zjednodušení ladění.

- [/Og](../../build/reference/og-global-optimizations.md) umožňuje globální optimalizace.

- [/OI](../../build/reference/oi-generate-intrinsic-functions.md) generuje vnitřní funkce pro příslušnou funkci volání.

- [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) určuje kompilátor upřednostnit optimalizace pro velikost přes optimalizace pro rychlost.

- [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (výchozí nastavení) informuje kompilátor upřednostnit optimalizace pro rychlost přes optimalizace pro velikost.

- [/Ox](../../build/reference/ox-full-optimization.md) je kombinace možnost, která vybere několik optimalizací s důrazem na rychlost. Je striktní podmnožinu **/O2** optimalizace.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) potlačí vytvoření ukazatele na rámce v zásobníku volání pro rychlejší volání funkce.

## <a name="remarks"></a>Poznámky

Můžete kombinovat více **/O** možnosti do příkazu jednu možnost. Například **/Odi** je stejný jako **/Od /Oi**. Některé možnosti se vzájemně vylučují a způsobit chyby kompilátoru, pokud použít společně. V tématu jednotlivých **/O** možnosti pro další informace.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)   
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)