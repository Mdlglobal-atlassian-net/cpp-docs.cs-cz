---
title: Konstanty haldy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _HEAPBADPTR
- _HEAPEMPTY
- _HEAPBADBEGIN
- _HEAPOK
- _HEAPBADNODE
- _HEAPEND
dev_langs: C++
helpviewer_keywords:
- _HEAPOK constants
- _HEAPEND constants
- HEAPBADBEGIN constants
- _HEAPBADNODE constants
- HEAPBADNODE constants
- HEAPBADPTR constants
- _HEAPEMPTY constants
- HEAPEND constants
- HEAPOK constants
- HEAPEMPTY constants
- _HEAPBADBEGIN constants
- _HEAPBADPTR constants
- heap constants
ms.assetid: 3f751bb9-2dc4-486f-b5f5-9061c96d3754
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2e1a15b371aa4f2997d453e2543123b279ac0df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="heap-constants"></a>Konstanty haldy
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <malloc.h>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto konstanty poskytnout návratovou hodnotu, která určuje stav haldě.  
  
|Konstanta|Význam|  
|--------------|-------------|  
|`_HEAPBADBEGIN`|Informace počáteční hlavičky nebyl nalezen nebo je neplatný.|  
|`_HEAPBADNODE`|Byl nalezen chybný uzel, nebo je poškozena halda.|  
|`_HEAPBADPTR`|**_pentry** pole z **_heapinfo –** struktura neobsahuje platný ukazatel do haldy (`_heapwalk` pouze rutiny).|  
|`_HEAPEMPTY`|Halda nebyla inicializována.|  
|`_HEAPEND`|Úspěšně byl dosažen konec haldy (`_heapwalk` pouze rutiny).|  
|`_HEAPOK`|Halda představuje konzistentní (`_heapset` a `_heapchk` pouze rutiny). Žádné chyby, pokud; **_Heapinfo –** struktura obsahuje informace o další položka (`_heapwalk` pouze rutiny).|  
  
## <a name="see-also"></a>Viz také  
 [_heapchk –](../c-runtime-library/reference/heapchk.md)   
 [_heapset –](../c-runtime-library/heapset.md)   
 [_heapwalk –](../c-runtime-library/reference/heapwalk.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)