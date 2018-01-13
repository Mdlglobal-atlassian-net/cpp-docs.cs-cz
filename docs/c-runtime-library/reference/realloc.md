---
title: "realloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: realloc
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
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
dev_langs: C++
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 525b0f0877471b5bfd6d9fa16551b21908f229a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="realloc"></a>realloc
Změnit přidělení bloků paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *realloc(  
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Ukazatel na dříve přidělenou paměť bloku.  
  
 `size`  
 Nová velikost v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 `realloc`Vrátí `void` ukazatel na oblast paměti opětovnému přidělení (a případně přesouvat).  
  
 Pokud není k dispozici dostatek paměti k rozšíření na danou velikost bloku, původní blok je vlevo beze změny, a `NULL` je vrácen.  
  
 Pokud `size` nula, pak je blok, na kterou odkazuje `memblock` uvolněno; vrácená hodnota je `NULL`, a `memblock` je ponechán jednotka ukazovat na uvolněné blok.  
  
 Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ jinými než `void`, používat typ, který přetypovat na návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `realloc` Funkce se změní velikost bloku přidělené paměti. `memblock` Argument odkazuje na začátku bloku paměti. Pokud `memblock` je `NULL`, `realloc` se chová stejně jako `malloc` a přiděluje nový blok `size` bajtů. Pokud `memblock` není `NULL`, by mělo být ukazatel vrácené z předchozího volání `calloc`, `malloc`, nebo `realloc`.  
  
 `size` Argument poskytuje novou velikost bloku, v bajtech. Obsah bloku jsou stejné až kratší velikostí novém i starém, i když může být nový blok v jiném umístění. Vzhledem k nového bloku můžou být nové umístění paměti, ukazatele vrácený `realloc` nemusí být předána ukazatele `memblock` argument. `realloc`nemá nulový počet nově přidělených paměti v případě růstu vyrovnávací paměti.  
  
 `realloc`Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo velikost paměti požadované překračuje `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `realloc`volání `malloc` Chcete-li použít C++ [_set_new_mode –](../../c-runtime-library/reference/set-new-mode.md) funkce nastavit nový režim obslužné rutiny. Nový režim obslužná rutina označuje, jestli při selhání, `malloc` je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md). Ve výchozím nastavení `malloc` nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když `realloc` nepodaří přidělit paměť, `malloc` volání nové rutiny obslužná rutina ve stejné způsobem, jako `new` operátor nepodporuje, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí nastavení, volejte  
  
```  
_set_new_mode(1)  
```  
  
 časná v těch, které jsou program nebo odkaz s NEWMODE. OBJ (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `realloc` přeloží na [_realloc_dbg –](../../c-runtime-library/reference/realloc-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `realloc`je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že není k úpravě globálních proměnných, že ukazatele vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`realloc`|\<stdlib.h > a \<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_realloc.c  
// This program allocates a block of memory for  
// buffer and then uses _msize to display the size of that  
// block. Next, it uses realloc to expand the amount of  
// memory used by buffer and then calls _msize again to  
// display the new amount of memory allocated to buffer.  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   long *buffer, *oldbuffer;  
   size_t size;  
  
   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )  
      exit( 1 );  
  
   size = _msize( buffer );  
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );  
  
   // Reallocate and show new size:  
   oldbuffer = buffer;     // save pointer in case realloc fails  
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))   
        ==  NULL )  
   {  
      free( oldbuffer );  // free original block  
      exit( 1 );  
   }  
   size = _msize( buffer );  
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",   
            size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after malloc of 1000 longs: 4000  
Size of block after realloc of 1000 more longs: 8000  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)