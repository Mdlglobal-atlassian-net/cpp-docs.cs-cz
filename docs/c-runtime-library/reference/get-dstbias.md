---
title: "_get_dstbias – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
dev_langs:
- C++
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4f6d43b904b96f7323c76637d1f38c024d4696f1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="getdstbias"></a>_get_dstbias
Načte posun na letní čas v sekundách.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      error_t _get_dstbias(   
    int* seconds  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seconds`  
 Posun v sekundách letní čas.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu nebo `errno` hodnotu, pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `_get_dstbias` Funkce načte počtem sekund za letní čas jako celé číslo. Pokud platí letní čas, výchozí posun je 3 600 sekund, což je počet sekund za jednu hodinu (i když několik oblastí sledovat posun dvou hodin).  
  
 Pokud `seconds` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `EINVAL`.  
  
 Doporučujeme, abyste tuto funkci použít místo makro `_dstbias` nebo zastaralé funkce `__dstbias`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_dstbias`|\<time.h>|  
  
 Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Správa času](../../c-runtime-library/time-management.md)   
 [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [_get_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [_get_tzname](../../c-runtime-library/reference/get-tzname.md)