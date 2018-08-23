---
title: smyčka | Dokumentace Microsoftu
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
ms.openlocfilehash: 7e4881dfdcb92e778501982482abc13cc91836b0
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466093"
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
  
### <a name="parameters"></a>Parametry  
*hint_parallel(n)*  
Dává pokyn kompilátoru, že tato smyčka měla být paralelizována přes *n* vláken, ve kterém *n* je kladný celočíselný literál nebo nula. Pokud *n* je nula, maximální počet vláken se používá v době běhu. To je pokyn kompilátoru, ne příkaz, a není zaručeno, že tato smyčka bude paralelizována. Pokud má smyčka závislosti na datech nebo strukturální problémy, tato smyčka například ukládá do skaláru, který je použit mimo tělo smyčky, nebude smyčka paralelizována.  
  
Kompilátor ignoruje tuto možnost, pokud [/Qpar](../build/reference/qpar-auto-parallelizer.md) je zadán přepínač kompilátoru.  
  
*no_vector*  
Ve výchozím nastavení je automatický vektorizér zapnutý a pokusí se vektorizovat všechny smyčky, které vyhodnotí, že budou užitečné. Zadáním této direktivy pragma zakážete automatickou vektorizaci smyčky, která jej následuje.  
  
*ivdep*  
Dá pokyn kompilátoru ignorovat závislosti vektorů pro tuto smyčku. Toto použijte ve spojení s *hint_parallel*.  
  
## <a name="remarks"></a>Poznámky  
 
Použít **smyčky** – Direktiva pragma, umístěte ji těsně před – není v – definici smyčky. Tato direktiva pragma se projeví v rozsahu smyčky, která ji následuje. Smyčce lze zadat více direktiv pragma v libovolném pořadí, ale je nutné každou z nich uvést v samostatném výrazu direktivy pragma.  
  
## <a name="see-also"></a>Viz také  
 
[Automatická paralelizace a Automatická vektorizace](../parallel/auto-parallelization-and-auto-vectorization.md)   
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)