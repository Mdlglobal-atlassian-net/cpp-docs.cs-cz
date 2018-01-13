---
title: "_realloc_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
dev_langs: C++
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3885bfb44745d815e50012d0447060b6ff2aa985
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="reallocdbg"></a>_realloc_dbg
Zadaný blok paměti v haldě přidělí přesunutí nebo změna velikosti bloku (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_realloc_dbg(  
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Ukazatel na dříve přidělenou paměť bloku.  
  
 `newSize`  
 Požadovaná velikost reallocated bloku (v bajtech).  
  
 `blockType`  
 Požadovaný typ pro reallocated blok: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který vyžadují `realloc` operace nebo hodnotu NULL.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor kde `realloc` operace byla požadovaná nebo má hodnotu NULL.  
  
 `filename` a `linenumber` parametry jsou k dispozici pouze při `_realloc_dbg` explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md) preprocesoru konstanta byla definována.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení této funkce buď vrací ukazatel na část uživatele k opětovnému přidělení paměti bloku, volá nové funkce obslužné rutiny nebo vrátí hodnotu NULL. Úplný popis návratový chování najdete v následující části poznámky. Další informace o používání nové funkce obslužné rutiny najdete v tématu [realloc –](../../c-runtime-library/reference/realloc.md) funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_realloc_dbg`ladicí verze [realloc –](../../c-runtime-library/reference/realloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_realloc_dbg` byla snížena volání `realloc`. Obě `realloc` a `_realloc_dbg` znovu přidělte blok paměti základní haldy, ale `_realloc_dbg` může vyrovnávat několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování konkrétní typy přidělování a `filename` / `linenumber` informací k určení původu požadavků na přidělení.  
  
 `_realloc_dbg`přidělí blok zadaná paměťová se něco víc místa, než požadovaný `newSize`. `newSize`může být větší nebo menší než velikost bloku původně přidělenou paměť. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Přerozdělení může způsobit přesunutí původní bloku paměti do jiného umístění v haldě, jakož i změníte velikost bloku paměti. Pokud se přesune bloku paměti, obsah původního bloku se přepíší.  
  
 `_realloc_dbg`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo pokud přesahuje množství paměti nutné (včetně režie, již bylo zmíněno dříve) `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_realloc_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [_msize_dbg –](../../c-runtime-library/reference/msize-dbg.md) tématu.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)