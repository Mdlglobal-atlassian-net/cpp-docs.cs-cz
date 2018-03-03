---
title: _daylight, _dstbias, _timezone a _tzname | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
dev_langs:
- C++
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81ab3701ac99aece4710208a0a5d19ce645d287a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone a _tzname
`_daylight`, `_dstbias`, `_timezone`, a `_tzname` se používají v některé rutiny datum a čas, aby úpravy místního času. Tyto globální proměnné jsou zastaralé pro bezpečnější funkční verze, které se mají používat místo globální proměnné.  
  
|Globální proměnná|Ekvivalentní|  
|---------------------|---------------------------|  
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|  
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|  
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|  
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|  
  
 Jsou deklarovány v Time.h následujícím způsobem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extern int _daylight;   
extern int _dstbias;   
extern long _timezone;   
extern char *_tzname[2];  
```  
  
## <a name="remarks"></a>Poznámky  
 Pro volání na `_ftime`, `localtime`, nebo `_tzset`, hodnoty `_daylight`, `_dstbias`, `_timezone`, a `_tzname` určuje od hodnoty `TZ` proměnné prostředí. Pokud nenastavíte explicitně hodnotu `TZ`, `_tzname[0]` a `_tzname[1]` obsahují výchozí nastavení "PST" a "PDT" v uvedeném pořadí.  Funkce čas zpracování ([_tzset –](../c-runtime-library/reference/tzset.md), [_ftime –](../c-runtime-library/reference/ftime-ftime32-ftime64.md), a [místní čas](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) pokus o nastavení hodnoty `_daylight`, `_dstbias` a `_timezone` podle dotaz na operační systém pro výchozí hodnota pro každou proměnnou. V následující tabulce jsou uvedeny hodnoty globální proměnné časového pásma.  
  
|Proměnná|Hodnota|  
|--------------|-----------|  
|`_daylight`|Nenulové hodnoty, pokud je zóna letní čas (DST) zadané v `TZ` nebo určené z operačního systému,, jinak hodnota 0. Výchozí hodnota je 1.|  
|`_dstbias`|Posun na letní čas.|  
|`_timezone`|Rozdíl v sekundách mezi místním a koordinovaného světového času. Výchozí hodnota je 28 800.|  
|`_tzname[0]`|Název časového pásma odvozené z `TZ` proměnné prostředí. Výchozí hodnota je "PST".|  
|`_tzname[1]`|Název zóny DST odvozené z `TZ` proměnné prostředí. Výchozí hodnota je "PDT" (tichomořského letního času).|  
  
## <a name="see-also"></a>Viz také  
 [Globální proměnné](../c-runtime-library/global-variables.md)   
 [_get_daylight –](../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias –](../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone –](../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../c-runtime-library/reference/get-tzname.md)