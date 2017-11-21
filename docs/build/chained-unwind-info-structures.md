---
title: "Zřetězené struktury Unwind Info | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 176835bf-f118-45d9-9128-9db4b7571864
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e608d3b6826eb8bfbcebdec7fdf9891d033b418
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="chained-unwind-info-structures"></a>Zřetězené struktury unwind info
Pokud je nastavený příznak UNW_FLAG_CHAININFO, pak je struktura unwind info je sekundární a pole sdílené výjimka – obslužná rutina/adresy zřetězené informace obsahuje primární unwind informace. Následující kód načítá primární unwind informace za předpokladu, že `unwindInfo` je nastaven příznak strukturu, která má UNW_FLAG_CHAININFO.  
  
```  
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);  
```  
  
 Zřetězené informace jsou užitečné v situacích, dva. Nejprve se může použít pro segmenty nesouvislé kódu. Pomocí zřetězené informace, můžete snížit velikost požadované unwind informací, protože nemáte duplicitní unwind kódů z primárního unwind info.  
  
 Zřetězené informace můžete použít také k seskupení volatile registrace uloží. Kompilátor může zdržet ukládání některé závislé registry, dokud nebude mimo prolog vstupu funkce. To můžete zaznamenat tak, že primární unwind informace pro část funkce před kód seskupené, a poté nastavením zřetězených informací s nenulovou velikostí prologu, kde unwind kódy ve zřetězených informacích odrážejí uložení stálé registry. V takovém případě jsou všechny instance UWOP_SAVE_NONVOL unwind kódy. Seskupení, které ukládá stálé registry pomocí PUSH nebo upraví konfigurace zaregistrovat pomocí další pevné přidělení zásobníku není podporována.  
  
 UNWIND_INFO položku, která má nastaven UNW_FLAG_CHAININFO může obsahovat položku RUNTIME_FUNCTION, jehož položka UNWIND_INFO také má nastaven UNW_FLAG_CHAININFO (vícenásobné zmenšující obalení). Nakonec zřetězené unwind informace, že budou doručeny ukazatele na položku UNWIND_INFO, který má UNW_FLAG_CHAININFO vymazán; Toto je primární položka UNWIND_INFO, která odkazuje na vstupní bod procedury skutečný.  
  
## <a name="see-also"></a>Viz také  
 [Unwind Data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)