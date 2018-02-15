---
title: "_get_timezone – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_timezone
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_timezone
- get_timezone
dev_langs:
- C++
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ee251c147fd0f3f34d229cafbbef28caf1cebd9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="gettimezone"></a>_get_timezone
Načte rozdíl v sekundách mezi místním a koordinovaný světový čas (UTC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      error_t _get_timezone(   
    long* seconds  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seconds`  
 Rozdíl v sekundách mezi místním ČASEM a.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu nebo `errno` hodnotu, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `_get_timezone` Funkce načte rozdíl v sekundách mezi místním ČASEM a jako celé číslo. Výchozí hodnota je 28 800 sekund pro Tichomořský běžný čas (8 hodin za čas UTC).  
  
 Pokud `seconds` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_timezone`|\<time.h>|  
  
 Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_tzname](../../c-runtime-library/reference/get-tzname.md)