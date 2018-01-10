---
title: "_calloc_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
dev_langs: C++
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4295dd84e8066de0906a6fcd7b154c94875f7f5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="callocdbg"></a>_calloc_dbg
Přidělí počet bloky paměti v haldě s další místo pro hlavičku ladění a přepsání vyrovnávací paměti (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_calloc_dbg(   
   size_t num,  
   size_t size,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `num`  
 Požadovaný počet bloky paměti.  
  
 `size`  
 Požadovaná velikost každého bloku paměti (v bajtech).  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu[typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo `NULL`.  
  
 `filename` a `linenumber` parametry jsou k dispozici pouze při `_calloc_dbg` explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md) preprocesoru konstanta byla definována.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení této funkce vrací ukazatel na části uživatele posledního bloku přidělenou paměť, volá nové funkce obslužné rutiny nebo vrátí `NULL`. Úplný popis návratový chování najdete v části poznámky. Další informace o používání nové funkce obslužné rutiny najdete v tématu [calloc –](../../c-runtime-library/reference/calloc.md) funkce.  
  
## <a name="remarks"></a>Poznámky  
 `_calloc_dbg`ladicí verze [calloc –](../../c-runtime-library/reference/calloc.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_calloc_dbg` byla snížena volání `calloc`. Obě `calloc` a `_calloc_dbg` přidělit `num` paměti bloků v haldě základní ale `_calloc_dbg` nabízí několik funkce ladění:  
  
-   Na obou stranách části uživatele bloku chcete otestovat nevracení vyrovnávací paměti.  
  
-   Parametr typ bloku ke sledování přidělení konkrétní typy.  
  
-   `filename`/`linenumber`informace k určení původu požadavků na přidělení.  
  
 `_calloc_dbg`přiděluje každého bloku paměti s něco víc místa, než požadovaný `size`. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Při přidělení bloku části uživatele bloku je vyplněnou hodnotou 0xCD a každý z vyrovnávací paměti přepsat jsou vyplněny 0xFD.  
  
 `_calloc_dbg`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti; `EINVAL` je vrácena, pokud objem paměti vyžadované (včetně režie, již bylo zmíněno dříve) přesahuje `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_calloc_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_callocd.c  
/*  
 * This program uses _calloc_dbg to allocate space for  
 * 40 long integers. It initializes each element to zero.  
 */  
#include <stdio.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
        long *bufferN, *bufferC;  
  
        /*   
         * Call _calloc_dbg to include the filename and line number  
         * of our allocation request in the header and also so we can  
         * allocate CLIENT type blocks specifically  
         */  
        bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );  
        bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );  
        if( bufferN != NULL && bufferC != NULL )  
              printf( "Allocated memory successfully\n" );  
        else  
              printf( "Problem allocating memory\n" );  
  
        /*   
         * _free_dbg must be called to free CLIENT type blocks  
         */  
        free( bufferN );  
        _free_dbg( bufferC, _CLIENT_BLOCK );  
}  
```  
  
```Output  
Allocated memory successfully  
```  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md)   
 [_DEBUG](../../c-runtime-library/debug.md)