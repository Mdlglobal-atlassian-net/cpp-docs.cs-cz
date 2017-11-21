---
title: "_malloc_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _malloc_dbg
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
- malloc_dbg
- _malloc_dbg
dev_langs: C++
helpviewer_keywords:
- malloc_dbg function
- memory allocation
- _malloc_dbg function
ms.assetid: c97eca51-140b-4461-8bd2-28965b49ecdb
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c578a60326a8606f207018804cc90a791d029239
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mallocdbg"></a>_malloc_dbg
Přiděluje blok paměti v haldě s další prostor pro ladění hlavičky a přepsání vyrovnávací paměti (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_malloc_dbg(  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `size`  
 Požadovaná velikost bloku paměti (v bajtech).  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo hodnota NULL.  
  
 `linenumber`  
 Číslo ve zdrojovém souboru, kde byla vyžádána operace přidělení řádku nebo hodnota NULL.  
  
 `filename` a `linenumber` parametry jsou k dispozici pouze při `_malloc_dbg` explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md) preprocesoru konstanta byla definována.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení této funkce vrací ukazatel na části uživatele bloku přidělenou paměť, volá nové funkce obslužné rutiny nebo vrátí hodnotu NULL. Úplný popis návratový chování najdete v následující části poznámky. Další informace o používání nové funkce obslužné rutiny najdete v tématu [malloc](../../c-runtime-library/reference/malloc.md) funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_malloc_dbg`ladicí verze [malloc](../../c-runtime-library/reference/malloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_malloc_dbg` byla snížena volání `malloc`. Obě `malloc` a `_malloc_dbg` přidělit blok paměti v haldě základní ale `_malloc_dbg` nabízí několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování konkrétní přidělení typy a `filename` / `linenumber` informací k určení původu požadavků na přidělení.  
  
 `_malloc_dbg`přiděluje blok paměti s něco víc místa, než požadovaný `size`. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Při přidělení bloku části uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.  
  
 `_malloc_dbg`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo pokud přesahuje množství paměti nutné (včetně režie, již bylo zmíněno dříve) `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_malloc_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
 Příklad, jak pomocí `_malloc_dbg`, najdete v části [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [_calloc_dbg –](../../c-runtime-library/reference/calloc-dbg.md)   
 [_calloc_dbg –](../../c-runtime-library/reference/calloc-dbg.md)