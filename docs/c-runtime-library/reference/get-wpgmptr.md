---
title: "_get_wpgmptr – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
dev_langs:
- C++
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8e272573db55e413d9654f1968f535b44dd5a7c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="getwpgmptr"></a>_get_wpgmptr
Získá aktuální hodnotu `_wpgmptr` – globální proměnná.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _get_wpgmptr(   
   wchar_t **pValue   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `pValue`  
 Ukazatel na řetězec tak, aby byla vyplněna s aktuální hodnota `_wpgmptr` proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nula v případě úspěšného; Kód chyby při selhání. Pokud `pValue` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 Volat pouze `_get_wpgmptr` Pokud má program široké vstupní bod, třeba `wmain()` nebo `wWinMain()`. `_wpgmptr` – Globální proměnná obsahuje úplnou cestu ke spustitelnému souboru spojených s procesem jako řetězec znaků celou. Další informace najdete v tématu [_pgmptr –, _wpgmptr –](../../c-runtime-library/pgmptr-wpgmptr.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_wpgmptr`|\<stdlib.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [_get_pgmptr](../../c-runtime-library/reference/get-pgmptr.md)
