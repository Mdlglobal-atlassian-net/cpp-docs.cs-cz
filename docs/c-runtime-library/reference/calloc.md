---
title: "calloc – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- calloc
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
- calloc
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f106ec1cd879282d557c492e4f19cdd01480575
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="calloc"></a>calloc
Pole v paměti přidělí u elementů na hodnotu 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *calloc(   
   size_t num,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `num`  
 Počet elementů.  
  
 `size`  
 Délka v bajtech jednotlivých prvků.  
  
## <a name="return-value"></a>Návratová hodnota  
 `calloc` vrací ukazatel na přidělené místo. Prostor úložiště ukazuje návratovou hodnotu záruku, že vhodně zarovnána pro ukládání jakéhokoli typu objektu. Získání ukazatele na typ jinými než `void`, používat typ, který přetypovat na návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `calloc` Funkce přidělí prostor úložiště pro pole `num` elementy, každý o délce `size` bajtů. Každý prvek je inicializován na hodnotu 0.  
  
 `calloc` Nastaví `errno` k `ENOMEM` Pokud selže přidělení paměti nebo velikost paměti požadované překračuje `_HEAP_MAXREQ`. Informace o tomto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 `calloc` volání `malloc` používat C++ [_set_new_mode –](../../c-runtime-library/reference/set-new-mode.md) funkce nastavit nový režim obslužné rutiny. Nový režim obslužná rutina označuje, jestli při selhání, `malloc` je volat nové rutiny obslužných rutin jako sady pomocí [_set_new_handler –](../../c-runtime-library/reference/set-new-handler.md). Ve výchozím nastavení `malloc` nevyvolá nové rutiny ovladače při selhání při přidělování paměti. Toto výchozí chování můžete přepsat tak, aby, když `calloc` nepodaří přidělit paměť, `malloc` volání nové rutiny obslužná rutina ve stejné způsobem, jako `new` operátor nepodporuje, když se nezdaří ze stejného důvodu. Chcete-li přepsat výchozí nastavení, volejte  
  
```  
_set_new_mode(1)  
```  
  
 časná v aplikaci nebo odkaz s NEWMODE. OBJ (viz [možnosti odkazů](../../c-runtime-library/link-options.md)).  
  
 Když aplikace je spojená s verzí ladicí běhové knihovny jazyka C, `calloc` přeloží na [_calloc_dbg –](../../c-runtime-library/reference/calloc-dbg.md). Další informace o spravováni haldě ladění během najdete v tématu [haldy ladění The CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 `calloc` je označena `__declspec(noalias)` a `__declspec(restrict)`, což znamená, že funkce záruku, že není k úpravě globálních proměnných, že ukazatele vrátí není alias. Další informace najdete v tématu [noalias](../../cpp/noalias.md) a [omezit](../../cpp/restrict.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`calloc`|\<stdlib.h > a \<malloc.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_calloc.c  
// This program uses calloc to allocate space for  
// 40 long integers. It initializes each element to zero.  
  
#include <stdio.h>  
#include <malloc.h>  
  
int main( void )  
{  
   long *buffer;  
  
   buffer = (long *)calloc( 40, sizeof( long ) );  
   if( buffer != NULL )  
      printf( "Allocated 40 long integers\n" );  
   else  
      printf( "Can't allocate memory\n" );  
   free( buffer );  
}  
```  
  
```Output  
Allocated 40 long integers  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [Volné](../../c-runtime-library/reference/free.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)