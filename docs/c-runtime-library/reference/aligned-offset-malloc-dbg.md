---
title: _aligned_offset_malloc_dbg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_offset_malloc_dbg
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
- _aligned_offset_malloc_dbg
- aligned_offset_malloc_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_offset_malloc_dbg function
- aligned_offset_malloc_dbg function
ms.assetid: 6c242307-c59e-4d63-aae5-d8cbec8e021c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc5ec74619f358dbbad27e0bed47115982d5da4e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="alignedoffsetmallocdbg"></a>_aligned_offset_malloc_dbg
Přidělí paměť na hranici zadané zarovnání (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _aligned_offset_malloc_dbg(  
   size_t size,   
   size_t alignment,   
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `size`  
 Velikost velikost paměti požadované přidělení.  
  
 [in] `alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
 [in] `offset`  
 Posun do přidělení paměti vynutit zarovnání.  
  
 [in] `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo hodnota NULL.  
  
 [in] `linenumber`  
 Číslo ve zdrojovém souboru, kde byla vyžádána operace přidělení řádku nebo hodnota NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatele na blok paměti, který byl přidělen nebo `NULL` Pokud operace se nezdařila.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_offset_malloc_dbg` ladicí verze [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_aligned_offset_malloc_dbg` byla snížena volání `_aligned_offset_malloc`. Obě `_aligned_offset_malloc` a `_aligned_offset_malloc_dbg` přidělit blok paměti v haldě základní ale `_aligned_offset_malloc_dbg` nabízí několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování konkrétní přidělení typy a `filename` / `linenumber` informací k určení původu požadavků na přidělení.  
  
 `_aligned_offset_malloc_dbg` přiděluje blok paměti s něco víc místa, než požadovaný `size`. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Při přidělení bloku části uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.  
  
 `_aligned_offset_malloc_dbg` je užitečné v situacích, kde je potřeba zarovnání vnořený elementu; například na vnořené třídy se potřeby zarovnání.  
  
 `_aligned_offset_malloc_dbg` je založena na `malloc`; Další informace najdete v tématu [malloc –](../../c-runtime-library/reference/malloc.md).  
  
 Tato funkce nastaví `errno` k `ENOMEM` Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost `_HEAP_MAXREQ`. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc `_aligned_offset_malloc` ověří jeho parametry. Pokud `alignment` není mocninou 2 nebo, pokud `offset` je větší než nebo rovno `size` a nenulové hodnoty, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_offset_malloc_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)