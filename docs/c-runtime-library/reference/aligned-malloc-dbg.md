---
title: "_aligned_malloc_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_malloc_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_malloc_dbg
- aligned_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b035189a9ae07bc637a8ed92c0fd4a0d2847fa1e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="alignedmallocdbg"></a>_aligned_malloc_dbg
Přidělí paměť na hranici zadané zarovnání s další prostor pro ladění hlavičky a přepsání vyrovnávací paměti (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _aligned_malloc_dbg(  
    size_t size,   
    size_t alignment,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `size`  
 Velikost velikost paměti požadované přidělení.  
  
 [in] `alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
 [in] `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo hodnota NULL.  
  
 [in] `linenumber`  
 Číslo ve zdrojovém souboru, kde byla vyžádána operace přidělení řádku nebo hodnota NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatele na blok paměti, který byl přidělen nebo `NULL` Pokud operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_malloc_dbg` ladicí verze [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_aligned_malloc_dbg` byla snížena volání `_aligned_malloc`. Obě `_aligned_malloc` a `_aligned_malloc_dbg` přidělit blok paměti v haldě základní ale `_aligned_malloc_dbg` nabízí několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, a `filename` / `linenumber` informace k určení původu požadavků na přidělení.  
  
 `_aligned_malloc_dbg` přiděluje blok paměti s něco víc místa, než požadovaný `size`. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Při přidělení bloku části uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.  
  
 `_aligned_malloc_dbg` Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo pokud přesahuje množství paměti nutné (včetně režie, již bylo zmíněno dříve) `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc `_aligned_malloc_dbg` ověří jeho parametry. Pokud `alignment` není mocninou 2 nebo `size` rovná nule, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_malloc_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)