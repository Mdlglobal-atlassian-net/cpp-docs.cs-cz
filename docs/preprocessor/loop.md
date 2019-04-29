---
title: loop
ms.date: 10/18/2018
f1_keywords:
- loop_CPP
- vc-pragma.loop
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
ms.openlocfilehash: a1640881d98073381a941478f4b78177a95698d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411328"
---
# <a name="loop"></a>loop

Určuje, jak bude kód smyčky zohledněn pomocí automatického paralelizéru, anebo vylučuje smyčku z úvahy pomocí automatického vektorizéru.

## <a name="syntax"></a>Syntaxe

```
#pragma loop( hint_parallel(n) )
#pragma loop( no_vector )
#pragma loop( ivdep )
```

### <a name="parameters"></a>Parametry

*hint_parallel(n)*<br/>
Dává pokyn kompilátoru, že tato smyčka měla být paralelizována přes *n* vláken, ve kterém *n* je kladný celočíselný literál nebo nula. Pokud *n* je nula, maximální počet vláken se používá v době běhu. To je pokyn kompilátoru, ne příkaz, a není zaručeno, že tato smyčka bude paralelizována. Pokud má smyčka závislosti na datech nebo strukturální problémy, tato smyčka například ukládá do skaláru, který je použit mimo tělo smyčky, nebude smyčka paralelizována.

Kompilátor ignoruje tuto možnost, pokud [/Qpar](../build/reference/qpar-auto-parallelizer.md) je zadán přepínač kompilátoru.

*no_vector*<br/>
Ve výchozím nastavení je automatický vektorizér zapnutý a pokusí se vektorizovat všechny smyčky, které vyhodnotí, že budou užitečné. Zadáním této direktivy pragma zakážete automatickou vektorizaci smyčky, která jej následuje.

*ivdep*<br/>
Dá pokyn kompilátoru ignorovat závislosti vektorů pro tuto smyčku. Toto použijte ve spojení s *hint_parallel*.

## <a name="remarks"></a>Poznámky

Použít **smyčky** – Direktiva pragma, umístěte ji těsně před – není v – definici smyčky. Tato direktiva pragma se projeví v rozsahu smyčky, která ji následuje. Smyčce lze zadat více direktiv pragma v libovolném pořadí, ale je nutné každou z nich uvést v samostatném výrazu direktivy pragma.

## <a name="see-also"></a>Viz také:

[Automatická paralelizace a automatická vektorizace](../parallel/auto-parallelization-and-auto-vectorization.md)<br/>
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)