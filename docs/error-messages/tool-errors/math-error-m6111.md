---
title: "Chyba matematické operace M6111 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6111
dev_langs: C++
helpviewer_keywords: M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 204df0df4855fd2628a96ac326dd39c0d65151e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6111"></a>Chyba matematické operace M6111
podtečení zásobníku  
  
 Operaci s plovoucí desetinnou čárkou výsledkem podtečení zásobníku na koprocesor 287 8087. 387 nebo emulátor.  
  
 Tato chyba je způsobená často volání `long double` funkce, která nevrátí hodnotu. Například následující vygeneruje tuto chybu při kompilované a spusťte:  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 Program se ukončí s ukončovacím kódem 139.