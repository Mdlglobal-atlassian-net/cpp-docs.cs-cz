---
title: "_rozšířit lokalitu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs: C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 09906e3cdf8455a2a221601f475074a18a72b1b6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expand"></a>_expand
Změní velikost bloku paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_expand(   
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
 `_expand`vrací neplatný ukazatel k opětovnému přidělení paměti bloku. `_expand`, na rozdíl od `realloc`, nelze přesunout blok změnit jeho velikost. Proto, pokud je dostatek paměti k dispozici bez přesouvání, rozbalte položku bloku `memblock` parametru `_expand` je stejný jako návratovou hodnotu.  
  
 `_expand`Vrátí `NULL` při rozpoznání chyby při své činnosti. Například pokud `_expand` se používá ke zmenšení blok paměti, se může zjišťovat poškození v haldě malé bloku nebo bloku neplatný ukazatel a vrátit `NULL`.  
  
 Pokud je rozšíření bloku na danou velikost bez přesouvání je k dispozici dostatek paměti, funkce vrátí hodnotu `NULL`. `_expand`nikdy vrátí blok rozšířit na velikost menší než požadovaný. Pokud dojde k selhání, `errno` označuje podstatu tohoto selhání. Další informace o `errno`, najdete v části [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Návratová hodnota odkazuje na prostor úložiště, který zaručeně vhodně zarovnána pro ukládání jakéhokoli typu objektu. Chcete-li zkontrolovat novou velikost položky, použijte `_msize`. Získání ukazatele na typ jinými než `void`, používat typ, který přetypovat na návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `_expand` Funkce změny velikosti bloku dříve přidělené paměti tak, že zkusíte rozbalit nebo sbalit bloku bez přesouvání její umístění v haldě. `memblock` Parametr odkazuje na začátku bloku. `size` Parametr poskytuje novou velikost bloku, v bajtech. Obsah bloku jsou stejné až kratší velikostí novém i starém. `memblock`by neměl být blok bylo uvolněno.  
  
> [!NOTE]
>  Na 64bitových platformách `_expand` nemusí smlouvy bloku, pokud novou velikost je menší než aktuální velikost; zejména, pokud byl menší než 16 kB velikostí bloku, proto přidělené v haldě fragmentace nízká `_expand` opustí bloku beze změny a Vrátí `memblock`.  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `_expand` přeloží na [_expand_dbg –](../../c-runtime-library/reference/expand-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Tato funkce ověří jeho parametry. Pokud `memblock` je ukazatel s hodnotou null, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`. Pokud `size` je větší než `_HEAP_MAXREQ`, `errno` je nastaven na `ENOMEM` a funkce vrátí hodnotu `NULL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_expand`|\<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_expand.c  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char *bufchar;  
   printf( "Allocate a 512 element buffer\n" );  
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )  
      exit( 1 );  
   printf( "Allocated %d bytes at %Fp\n",   
         _msize( bufchar ), (void *)bufchar );  
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )  
      printf( "Can't expand" );  
   else  
      printf( "Expanded block to %d bytes at %Fp\n",   
            _msize( bufchar ), (void *)bufchar );  
   // Free memory   
   free( bufchar );  
   exit( 0 );  
}  
```  
  
```Output  
Allocate a 512 element buffer  
Allocated 512 bytes at 002C12BC  
Expanded block to 1024 bytes at 002C12BC  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [calloc –](../../c-runtime-library/reference/calloc.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [_msize –](../../c-runtime-library/reference/msize.md)   
 [realloc –](../../c-runtime-library/reference/realloc.md)