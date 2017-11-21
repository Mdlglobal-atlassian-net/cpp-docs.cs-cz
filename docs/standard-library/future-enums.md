---
title: "&lt;budoucí&gt; výčty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: 835abafde46858bd108dfa648a246345bd254eaf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltfuturegt-enums"></a>&lt;budoucí&gt; výčty
||||  
|-|-|-|  
|[future_errc](#future_errc)|[future_status](#future_status)|[spuštění](#launch)|  
  
##  <a name="future_errc"></a>future_errc – výčet  
 Poskytuje symbolické názvy pro všechny chyby, které jsou hlášeny [future_error](../standard-library/future-error-class.md) třídy.  
  
Třída future_errc {broken_promise, future_already_retrieved, promise_already_satisfied, no_state};  
  
##  <a name="future_status"></a>future_status – výčet  
 Poskytuje symbolické názvy z důvodů, které můžou vrátit funkce vypršel čekání.  
  
```
enum future_status{    ready,
    timeout,
 deferred};
```  
  
##  <a name="launch"></a>Launch – výčet  
 Představuje typ bitová maska, která popisuje možné režimy pro funkce šablony [asynchronní](../standard-library/future-functions.md#async).  
  
Třída spuštění {asynchronní, odložení};  
  
## <a name="see-also"></a>Viz také  
 [\<budoucí >](../standard-library/future.md)



