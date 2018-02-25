---
title: "smyčky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs:
- C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3e076c48b512c6059a2f574a07f6e77acfaca22
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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