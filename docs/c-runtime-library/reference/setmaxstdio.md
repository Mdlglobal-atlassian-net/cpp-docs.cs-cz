---
title: _setmaxstdio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _setmaxstdio
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
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5317437202cef423759ac850aab2360892521746
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="setmaxstdio"></a>_setmaxstdio
Nastaví maximální počet současně otevřených souborů na `stdio` úroveň.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newmax`  
 Nové maximální počet současně otevřených souborů na `stdio` úroveň.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `newmax` v případě úspěšného; jinak hodnota -1.  
  
 Pokud `newmax` je menší než `_IOB_ENTRIES` nebo novější, je vyvolána maximální počet obslužných rutin, které jsou k dispozici v operačním systému, obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, tato funkce vrátí hodnotu -1 a nastaví je povoleno spuštění `errno` k `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_setmaxstdio` Funkce změní maximální hodnotu pro počet souborů, které může být najednou otevřený v `stdio` úroveň.  
  
 Vstupně-výstupních operací C Runtime teď podporuje mnoho více otevřených souborů na Win32 platformami než v předchozích verzích. Až 2 048 soubory lze otevřít současně na [lowio úroveň](../../c-runtime-library/low-level-i-o.md) (to znamená, otevřít a k němu přistupovat prostřednictvím `_open`, `_read`, `_write`, a tak dále rodiny funkcí vstupně-výstupních operací). Až 512 soubory lze otevřít současně na [stdio úroveň](../../c-runtime-library/stream-i-o.md) (to znamená, otevřít a k němu přistupovat prostřednictvím `fopen`, `fgetc`, `fputc`, a tak dále rodiny funkcí). Maximální počet 512 otevřených souborů na `stdio` úrovni je možné zvýšit na maximálně 2 048 prostřednictvím `_setmaxstdio` funkce.  
  
 Protože `stdio`-úroveň funkce, jako třeba `fopen`, jsou postavený na `lowio` funkce, je maximálně 2 048 pevný horní limit pro počet současně otevřených souborů, které jsou přístupné prostřednictvím běhové knihovny jazyka C.  
  
> [!NOTE]
>  Tento horní limit, může být dále, než je podporována v konkrétní Win32 platformy a konfigurace.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_setmaxstdio`|\<stdio.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 V tématu [_getmaxstdio –](../../c-runtime-library/reference/getmaxstdio.md) příklad použití `_setmaxstdio`.  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)