---
title: "_get_fmode – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: abfdd4d9b8838914a91b4db995fcaad573e80829
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="getfmode"></a>_get_fmode
Získá výchozí režim překladu souboru pro soubor vstupně-výstupních operací.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _get_fmode(   
   int * pmode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `pmode`  
 Ukazatel na celé číslo, aby byla vyplněna s aktuální výchozí režim: `_O_TEXT` nebo `_O_BINARY`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí nula v případě úspěšného; Kód chyby při selhání. Pokud `pmode` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 Získá hodnotu funkce [_fmode –](../../c-runtime-library/fmode.md) – globální proměnná. Tato proměnná Určuje výchozí režim překladu souboru pro obě nízké úrovně a stream vstupně-výstupní operace, jako například `_open`, `_pipe`, `fopen`, a `freopen`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_get_fmode`|\<stdlib.h>|\<fcntl.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_set_fmode –](../../c-runtime-library/reference/set-fmode.md).  
  
## <a name="see-also"></a>Viz také  
 [_fmode](../../c-runtime-library/fmode.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)   
 [I/O soubor textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md)