---
title: "&lt;stdexcept –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <stdexcept>
dev_langs:
- C++
helpviewer_keywords:
- stdexcept header
ms.assetid: 495c10b1-1e60-4514-9f8f-7fda11a2f522
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26cc6c5811819ffcb909e2e27ab90e7dad1f19fc
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltstdexceptgt"></a>&lt;stdexcept&gt;
Definuje několik standardní třídy používané pro generování sestav výjimky. Třídy tvoří hierarchii odvození všechny odvozené od třídy [výjimka](../standard-library/exception-class.md) a zahrnují dva obecné typy výjimek: logické chyby a chyby. Logické chyby se nezdařila z důvodu programátory chyb. Že jsou odvozeny od základní třídy logic_error a zahrnují:  
  
-   `domain_error`  
  
-   `invalid_argument`  
  
-   `length_error`  
  
-   `out_of_range`  
  
 Běhové chyby dojít z důvodu chyby v knihovně funkce nebo v běhu systému. Že jsou odvozeny od základní třídy runtime_error a zahrnují:  
  
-   `overflow_error`  
  
-   `range_error`  
  
-   `underflow_error`  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[domain_error – třída](../standard-library/domain-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané domény chybové zprávě.|  
|[invalid_argument – třída](../standard-library/invalid-argument-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané nahlásit neplatný argument.|  
|[length_error – třída](../standard-library/length-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané nahlásit pokusu o generování příliš dlouhý, je třeba zadat objekt.|  
|[logic_error – třída](../standard-library/logic-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané zprávy o chybách pravděpodobně rozpoznat, před spuštěním programu, například porušení logické předběžné podmínky.|  
|[out_of_range – třída](../standard-library/out-of-range-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané nahlásit argument, který je mimo platný rozsah.|  
|[overflow_error – třída](../standard-library/overflow-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané nahlásit aritmetického přetečení.|  
|[range_error – třída](../standard-library/range-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané rozsah chybové zprávě.|  
|[runtime_error – třída](../standard-library/runtime-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vyvolána zprávy o chybách pravděpodobně rozpoznat pouze v případě, že se program spustí.|  
|[underflow_error – třída](../standard-library/underflow-error-class.md)|Třída slouží jako základní třída pro všechny výjimky vydané nahlásit aritmetické podtečení.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

