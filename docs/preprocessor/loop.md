---
title: loop – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: 013540ffe120f42c15538ce86661753b9cf9416f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220857"
---
# <a name="loop-pragma"></a>loop – direktiva pragma

Určuje, jak má být kód smyčky považován za auto-paralelizace, nebo vylučuje smyčku z úvahy pomocí auto-vektorizace.

## <a name="syntax"></a>Syntaxe

> **cyklus #pragma (hint_parallel (** *n* **))** \
> **cyklus #pragma (no_vector)** \
> **cyklus #pragma (ivdep)**

### <a name="parameters"></a>Parametry

**hint_parallel (** *n* **)** \
Pomocný parametr kompilátoru, že by se tato smyčka měla paralelně nacházet v *n* vláknech, kde *n* je kladný celočíselný literál nebo nula. Pokud *n* je nula, je v době běhu použit maximální počet vláken. Je to pomocný parametr kompilátoru, nikoli příkaz. Není nijak zaručeno, že smyčka bude paralelní. Pokud má smyčka závislosti dat nebo strukturální problémy, nebude se paralelně provádět. Nejedná se například o paralelní, pokud je uložen na skalární hodnotu, která je použita mimo tělo smyčky.

Kompilátor ignoruje tuto možnost, pokud není zadán přepínač kompilátoru [/Qpar](../build/reference/qpar-auto-parallelizer.md) .

**no_vector**\
Ve výchozím nastavení se automaticky vektorizace pokusí vektorizovaná všechny smyčky, které vyhodnotí. Zadáním této direktivy pragma zakážete automatické vektorizace pro smyčku, která následuje.

**ivdep**\
Pomocný parametr kompilátoru pro ignorování závislostí vektoru pro tuto smyčku. Tuto možnost použijte spolu s **hint_parallel**.

## <a name="remarks"></a>Poznámky

Chcete-li použít direktivu pragma **smyčky** , umístěte ji bezprostředně před, nikoli do definice smyčky. Tato direktiva pragma se projeví v rozsahu smyčky, která ji následuje. Smyčce lze zadat více direktiv pragma v libovolném pořadí, ale je nutné každou z nich uvést v samostatném výrazu direktivy pragma.

## <a name="see-also"></a>Viz také:

[Automatické Paralelismuy a automatické rozvektory](../parallel/auto-parallelization-and-auto-vectorization.md)\
[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
