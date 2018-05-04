---
title: Selhání háků | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be598a77ca48eeee03360a3b598b0567abc6ee4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="failure-hooks"></a>Selhání háků
Je povoleno hák selhání stejným způsobem jako [oznámení háku](../../build/reference/notification-hooks.md). Běžné potřeby háku vrátit vhodnou hodnotu tak, aby zpracování může pokračovat (HINSTANCE nebo FARPROC), nebo 0 k označení, že by měl být vyvolána výjimka.  
  
 Proměnné ukazatele, který odkazuje na uživatelem definované funkce je:  
  
```  
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}  
ExternC  
PfnDliHook   __pfnDliFailureHook2;  
```  
  
 **DelayLoadInfo** struktura obsahuje všechny relevantní data potřebná pro přesné vytváření sestav v chybě, včetně hodnot z `GetLastError`.  
  
 Pokud se oznámení o **dliFailLoadLib**, funkce háku může vrátit:  
  
-   0, pokud ji nemůže zpracovat selhání.  
  
-   HMODULE, pokud hák selhání opraven problém a načíst samotné knihovny.  
  
 Pokud se oznámení o **dliFailGetProc**, funkce háku může vrátit:  
  
-   0, pokud ji nemůže zpracovat selhání.  
  
-   Adresu platný proc (import funkce adresy), pokud selhání připojení úspěšně získávání samotnou adresu.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md)