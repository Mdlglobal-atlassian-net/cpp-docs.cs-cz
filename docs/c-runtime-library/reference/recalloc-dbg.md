---
title: "_recalloc_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
dev_langs: C++
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 02ac41e22a5080576339b00e54f339bb878a794d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recallocdbg"></a>_recalloc_dbg
Přidělí pole a inicializuje jeho prvky na hodnotu 0 (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_recalloc_dbg(   
   void *userData,  
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `userData`  
 Ukazatel na dříve přidělenou paměť bloku.  
  
 `num`  
 Požadovaný počet bloky paměti.  
  
 `size`  
 Požadovaná velikost každého bloku paměti (v bajtech).  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo `NULL`.  
  
 `filename` a `linenumber` parametry jsou k dispozici pouze při `_recalloc_dbg` explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md) preprocesoru konstanta byla definována.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení této funkce buď vrací ukazatel na část uživatele k opětovnému přidělení paměti bloku, volá nové funkce obslužné rutiny nebo vrátí hodnotu NULL. Úplný popis návratový chování najdete v následující části poznámky. Další informace o používání nové funkce obslužné rutiny najdete v tématu [_recalloc –](../../c-runtime-library/reference/recalloc.md) funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_recalloc_dbg`ladicí verze [_recalloc –](../../c-runtime-library/reference/recalloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_recalloc_dbg` byla snížena volání `_recalloc`. Obě `_recalloc` a `_recalloc_dbg` znovu přidělte blok paměti základní haldy, ale `_recalloc_dbg` může vyrovnávat několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování konkrétní typy přidělování a `filename` / `linenumber` informací k určení původu požadavků na přidělení.  
  
 `_recalloc_dbg`přidělí blok zadaná paměťová se něco víc místa, než požadovaná velikost (`num` * `size`) který může být větší nebo menší než velikost bloku původně přidělenou paměť. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Přerozdělení může způsobit přesunutí původní bloku paměti do jiného umístění v haldě, jakož i změníte velikost bloku paměti. Část uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.  
  
 `_recalloc_dbg`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti; `EINVAL` je vrácena, pokud objem paměti vyžadované (včetně režie, již bylo zmíněno dříve) přesahuje `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_recalloc_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)