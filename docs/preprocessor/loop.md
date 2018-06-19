---
title: smyčky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs:
- C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9af0e01cd29d6fe89e0cd0d6c5ff4a7030909799
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846529"
---
# <a name="loop"></a>loop
Určuje, jak bude kód smyčky zohledněn pomocí automatického paralelizéru, anebo vylučuje smyčku z úvahy pomocí automatického vektorizéru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### <a name="parameters"></a>Parametry  
 `hint_parallel(` `n` `)`  
 Dává pokyn kompilátoru, že by tato smyčka měla být paralelizována přes `n` vláken, kde `n` je kladný celočíselný literál nebo nula. Pokud je `n` nula, je v době spuštění použit maximální počet vláken. To je pokyn kompilátoru, ne příkaz, a není zaručeno, že tato smyčka bude paralelizována. Pokud má smyčka závislosti na datech nebo strukturální problémy, tato smyčka například ukládá do skaláru, který je použit mimo tělo smyčky, nebude smyčka paralelizována.  
  
 Kompilátor ignoruje tuto možnost, pokud [/Qpar](../build/reference/qpar-auto-parallelizer.md) je zadán přepínač kompilátoru.  
  
 `no_vector`  
 Ve výchozím nastavení je automatický vektorizér zapnutý a pokusí se vektorizovat všechny smyčky, které vyhodnotí, že budou užitečné. Zadáním této direktivy pragma zakážete automatickou vektorizaci smyčky, která jej následuje.  
  
 `ivdep`  
 Dá pokyn kompilátoru ignorovat závislosti vektorů pro tuto smyčku. Toto použijte ve spojení s `hint_parallel`.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li použít direktivu pragma `loop`, umístěte ji těsně před definici smyčky, ne dovnitř. Tato direktiva pragma se projeví v rozsahu smyčky, která ji následuje. Smyčce lze zadat více direktiv pragma v libovolném pořadí, ale je nutné každou z nich uvést v samostatném výrazu direktivy pragma.  
  
## <a name="see-also"></a>Viz také  
 [Automatická paralelizace a Automatická vektorizace](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)