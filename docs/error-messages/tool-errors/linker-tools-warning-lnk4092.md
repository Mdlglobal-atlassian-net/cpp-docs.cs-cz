---
title: "Upozornění linkerů Lnk4092 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a25954b8dc15863a290bd5a99119cc79a5585e16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4092"></a>Upozornění linkerů LNK4092
sdílené zapisovatelné obsahuje relocations; 'části. bitová kopie nemusí správně fungovat.  
  
 Linkeru vysílá toto upozornění pokaždé, když máte sdílený oddíl s upozorněním na potenciálně vážný problém.  
  
 Jedním ze způsobů sdílení dat mezi několika procesů je k označení oddíl jako "sdílené". Označení oddílu jako sdílené může způsobit problémy. Máte například knihovny DLL, která obsahuje deklarace takto sdílené datové části:  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 Nelze vyřešit linkeru `pvar` protože její hodnota závisí na kde knihovnu DLL je načten do paměti, takže uloží záznam přemístění v knihovně DLL. Když knihovnu DLL je načten do paměti, adresu `var` lze vyřešit a `pvar` přiřazen. Pokud jiný proces stejnou knihovnu DLL načte, ale nemůže načíst zároveň adresu, přemístění adresu `var` zaktualizuje pro druhý proces a proces první adresní prostor bude odkazovat na nesprávnou adresu.