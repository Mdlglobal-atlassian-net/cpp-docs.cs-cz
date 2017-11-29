---
title: "steady_clock – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: chrono/std::chrono::steady_clock
dev_langs: C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4fa9b54e4fb65fe9e3309b06c87dc713df92ec16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="steadyclock-struct"></a>steady_clock – struktura
Představuje `steady` hodiny.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct steady_clock;  
```  
  
## <a name="remarks"></a>Poznámky  
 V systému Windows steady_clock – zabalí funkci QueryPerformanceCounter.  
  
 Hodiny, které je *monotónní* Pokud hodnotu, která je vrácen první volání `now()` je vždy menší než nebo rovna hodnotu, která je vrácena voláním následné `now()`.  
  
 Hodiny, které je *konstantní* Pokud je *monotónní* a pokud je doba mezi počtu taktů konstantní.  
  
 High_resolution_clock je typdef pro steady_clock –.  
  
## <a name="public-functions"></a>Veřejné funkce  
  
|Funkce|Popis|  
|--------------|-----------------|  
|Nyní|Vrátí aktuální čas jako hodnotu time_point.|  
  
## <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|`system_clock::is_steady`|Obsahuje `true`. A `steady_clock` je *konstantní*.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<typu chrono >  
  
 **Namespace:** std::chrono  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [\<typu chrono >](../standard-library/chrono.md)   
 [system_clock – struktura](../standard-library/system-clock-structure.md)