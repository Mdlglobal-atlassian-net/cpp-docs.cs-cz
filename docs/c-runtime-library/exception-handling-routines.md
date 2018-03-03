---
title: "Rutiny zpracování výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95ecbc69dd9cbd86bd7891c79f115442f659ff94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exception-handling-routines"></a>Rutiny zpracování výjimek
Zpracování výjimek funkcí jazyka C++ použijte k obnovení z neočekávané události při spuštění programu.  
  
### <a name="exception-handling-functions"></a>Zpracování výjimek – funkce  
  
|Funkce|Použití|  
|--------------|---------|  
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Win32 zpracování výjimek (C strukturovaná výjimky) jako C++ zadali výjimky|  
|[set_terminate –](../c-runtime-library/reference/set-terminate-crt.md)|Nainstalovat rutiny vlastní ukončení má být volána`terminate`|  
|[set_unexpected –](../c-runtime-library/reference/set-unexpected-crt.md)|Instalace funkce vlastní ukončení má být volána`unexpected`|  
|[ukončení](../c-runtime-library/reference/terminate-crt.md)|Volá automaticky za určitých okolností se po vyvolání výjimky. `terminate` Volání funkce `abort` nebo funkci, můžete zadat pomocí`set_terminate`|  
|[neočekávané](../c-runtime-library/reference/unexpected-crt.md)|Volání `terminate` nebo funkci, můžete zadat pomocí `set_unexpected`. `unexpected` Funkce ještě není používáno ve aktuální implementace zpracování výjimek Microsoft C++|  
  
## <a name="see-also"></a>Viz také  
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)