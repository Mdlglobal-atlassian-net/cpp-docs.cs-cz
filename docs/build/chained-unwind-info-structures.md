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
ms.workload: cplusplus
ms.openlocfilehash: 3ac09c1f107b51542b7a17c8661eb784b4abf14a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [Unwind data pro zpracování výjimek, podpora ladění](../build/unwind-data-for-exception-handling-debugger-support.md)