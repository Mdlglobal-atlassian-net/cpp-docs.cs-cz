---
title: "volné | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: free
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords: free
dev_langs: C++
helpviewer_keywords:
- memory blocks, deallocating
- free function
ms.assetid: 74ded9cf-1863-432e-9306-327a42080bb8
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 61d750fce6e31923636b4eb8c0181bf405b7be39
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="free"></a>free
Zruší přidělení nebo uvolní blok paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void free(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Dříve při přidělování paměti bloku na uvolnění.  
  
## <a name="remarks"></a>Poznámky  
 `free` Funkce zruší přidělení paměti blok (`memblock`), již bylo přiděleno voláním `calloc`, `malloc`, nebo `realloc`. Počet bajtů, uvolněné se rovná počet bajtů, které jsou požadovány při bloku byl přidělen (nebo opětovnému přidělení u `realloc`). Pokud `memblock` je `NULL`, ukazatele je ignorován a `free` hned vrátí. Probíhá pokus o volné neplatný ukazatel (ukazatel na blok paměti, která nebyla přidělena `calloc`, `malloc`, nebo `realloc`) může mít vliv na následné přidělení požadavky a způsobit chyby.  
  
 Pokud dojde k chybě v uvolnění paměti, `errno` je nastaven s informacemi z operačního systému, o povaze chyby. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Po blok paměti bylo uvolněno, [_heapmin –](../../c-runtime-library/reference/heapmin.md) minimalizuje množství volné paměti v haldě slučování nepoužívané oblasti a uvolnění je zpět do operačního systému. Uvolněné paměti, které není vydané v operačním systému je obnovit do volného fondu a je k dispozici pro přidělení znovu.  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `free` přeloží na [_free_dbg –](../../c-runtime-library/reference/free-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `free`je označena `__declspec(noalias)`, což znamená, že funkce záruku, že nechcete upravit globální proměnné. Další informace najdete v tématu [noalias](../../cpp/noalias.md).  
  
 Uvolnit paměť, kterým je přiřazen [_malloca –](../../c-runtime-library/reference/malloca.md), použijte [_freea –](../../c-runtime-library/reference/freea.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`free`|\<stdlib.h > a \<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [malloc –](../../c-runtime-library/reference/malloc.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [_alloca –](../../c-runtime-library/reference/alloca.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg –](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin –](../../c-runtime-library/reference/heapmin.md)   
 [_freea –](../../c-runtime-library/reference/freea.md)