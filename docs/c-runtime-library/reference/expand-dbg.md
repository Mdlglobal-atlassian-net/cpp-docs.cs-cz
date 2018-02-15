---
title: "_expand_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41f3d59cec6ec4a064143e0211ebd956f30e16e5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="expanddbg"></a>_expand_dbg
Změní velikost zadaný blok paměti v haldě rozšiřování nebo smluvní blok (pouze ladicí verze).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_expand_dbg(   
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
 Požadovaný novou velikost bloku (v bajtech).  
  
 `blockType`  
 Požadovaný typ pro změněnou blok: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který vyžadují rozbalte operaci nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace rozbalte nebo `NULL`.  
  
 `filename` a `linenumber` parametry jsou k dispozici pouze při `_expand_dbg` explicitně volané nebo [_crtdbg_map_alloc –](../../c-runtime-library/crtdbg-map-alloc.md) preprocesoru konstanta byla definována.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při úspěšném dokončení `_expand_dbg` vrací ukazatel na blok změněnou velikostí paměti. Vzhledem k tomu, že paměť není přesunut, adresa je stejný jako userData. Pokud došlo k chybě nebo bloku nelze rozbalit na požadovanou velikost, vrátí `NULL`. Pokud dojde k selhání, `errno` je s informacemi z operačního systému, o povaze chyby. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_expand_dbg` Funkce je ladicí verze _[rozbalte](../../c-runtime-library/reference/expand.md) funkce. Když [_DEBUG –](../../c-runtime-library/debug.md) není definován, každé volání `_expand_dbg` byla snížena volání `_expand`. Obě `_expand` a `_expand_dbg` změnit velikost bloku paměti základní haldy, ale `_expand_dbg` může vyrovnávat několik funkce ladění: vyrovnávací paměti na obou stranách části uživatele bloku chcete otestovat nevracení, parametr typ bloku ke sledování konkrétní přidělení typy a `filename` / `linenumber` informací k určení původu požadavků na přidělení.  
  
 `_expand_dbg` Změní velikost bloku zadaná paměťová se něco víc místa, než požadovaný `newSize`. `newSize` může být větší nebo menší než velikost bloku původně přidělenou paměť. Další prostor se používá správce haldy ladění propojení bloky paměti ladění a k poskytování aplikace s informace o ladění záhlaví a přepsat vyrovnávací paměti. Změna provádí rozšiřování či smluvní původní bloku paměti. `_expand_dbg` nepřesouvá bloku paměti, stejně jako [_realloc_dbg –](../../c-runtime-library/reference/realloc-dbg.md) funkce.  
  
 Když `newSize` je větší než původní bloku je velikost bloku paměti rozšířena. Během rozšiřování, pokud blok paměti nelze rozšířit tak, aby dokázala pojmout požadovanou velikost `NULL` je vrácen. Když `newSize` je menší než původní blok velikost bloku paměti sjednané dokud novou velikost.  
  
 Informace o tom, jak jsou bloky paměti přidělené, inicializovat a spravovat ladicí verze základní heap najdete v tématu [podrobnosti haldy ladění CRT](/visualstudio/debugger/crt-debug-heap-details). Informace o typech bloku přidělení a způsobu jejich použití naleznete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details). Informace o rozdílech mezi volání funkce standardní haldy a jeho ladicí verze v sestavení ladicí verze aplikace, najdete v tématu [ladění verzí z funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
 Tato funkce ověří jeho parametry. Pokud `memblock` je ukazatel s hodnotou null, nebo pokud je větší než velikost `_HEAP_MAXREQ`, tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_expand_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md) pouze.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _expand_dbg of 1 more long: 164  
```  
  
## <a name="comment"></a>Komentář  
 Výstup tohoto programu, závisí na počítače umožňuje rozšířit všechny oddíly. Pokud jsou všechny části rozšiřovat, výstup se projeví v sekci Výstup.  
  
## <a name="see-also"></a>Viz také  
 [Rutiny ladění](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)