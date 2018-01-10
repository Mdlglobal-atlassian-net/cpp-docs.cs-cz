---
title: "_aligned_offset_realloc_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _aligned_offset_realloc_dbg
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
- aligned_offset_realloc_dbg
- _aligned_offset_realloc_dbg
dev_langs: C++
helpviewer_keywords:
- aligned_offset_realloc_dbg function
- _aligned_offset_realloc_dbg function
ms.assetid: 64e30a12-887e-453b-aea8-aed793fca9d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3dc1530e52b7aebf74f538bf7d2b8499b82e5a5a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="alignedoffsetreallocdbg"></a>_aligned_offset_realloc_dbg
Změní velikost bloku paměti, který byl přidělen s [_aligned_malloc –](../../c-runtime-library/reference/aligned-malloc.md) nebo [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md) (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _aligned_offset_realloc_dbg(  
   void *memblock,   
   size_t size,   
   size_t alignment,  
   size_t offset,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`memblock`  
 Aktuální ukazatel bloku paměti.  
  
 [v]`size`  
 Velikost přidělení paměti.  
  
 [v]`alignment`  
 Zarovnání hodnota, která musí být celé číslo mocninou 2.  
  
 [v]`offset`  
 Posun do přidělení paměti vynutit zarovnání.  
  
 [v]`filename`  
 Ukazatel na název zdrojového souboru, který vyžadují `aligned_offset_realloc` operace nebo hodnotu NULL.  
  
 [v]`linenumber`  
 Číslo řádku na zdrojový soubor kde `aligned_offset_realloc` operace byla požadovaná nebo má hodnotu NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_aligned_offset_realloc_dbg`vrací neplatný ukazatel k opětovnému přidělení (a případně přesouvat) paměti bloku. Vrácená hodnota je `NULL` Pokud velikost je nula a argument vyrovnávací paměti není `NULL`, nebo pokud není k dispozici dostatek paměti k rozšíření bloku na danou velikost. V prvním případě původní blok uvolněno. V druhém případě je původní blok beze změny. Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ než void, použijte typ přetypovat na návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `_aligned_offset_realloc_dbg`ladicí verze [_aligned_offset_realloc –](../../c-runtime-library/reference/aligned-offset-realloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_aligned_offset_realloc_dbg` byla snížena volání `_aligned_offset_realloc`. Obě `_aligned_offset_realloc` a `_aligned_offset_realloc_dbg` znovu přidělte blok paměti základní haldy, ale `_aligned_offset_realloc_dbg` může vyrovnávat několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování konkrétní typy přidělování a `filename` / `linenumber` informací k určení původu požadavků na přidělení.  
  
 Jako [_aligned_offset_malloc –](../../c-runtime-library/reference/aligned-offset-malloc.md), `_aligned_offset_realloc_dbg` umožňuje struktura zarovnána na posun v rámci struktury.  
  
 `_realloc_dbg`přidělí blok zadaná paměťová se něco víc místa, než požadovaný `newSize`. `newSize`může být větší nebo menší než velikost bloku původně přidělenou paměť. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Přerozdělení může způsobit přesunutí původní bloku paměti do jiného umístění v haldě, jakož i změníte velikost bloku paměti. Pokud se přesune bloku paměti, obsah původního bloku se přepíší.  
  
 Tato funkce nastaví `errno` k `ENOMEM` Pokud přidělení paměti se nezdařilo nebo pokud byla větší než požadovaná velikost `_HEAP_MAXREQ`. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Navíc `_aligned_offset_realloc_dbg` ověří jeho parametry. Pokud `alignment` není mocninou 2 nebo, pokud `offset` je větší než nebo rovno `size` a nenulové hodnoty, tato funkce volá neplatný parametr obslužnou rutinu, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `NULL` a nastaví `errno` k `EINVAL`.  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_aligned_offset_realloc_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)