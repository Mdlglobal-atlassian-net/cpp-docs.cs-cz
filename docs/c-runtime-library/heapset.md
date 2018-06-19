---
title: _heapset – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _heapset
apilocation:
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _heapset
- heapset
dev_langs:
- C++
helpviewer_keywords:
- checking heap
- heapset function
- heaps, checking
- debugging [CRT], heap-related problems
- _heapset function
ms.assetid: 9667eeb0-55bc-4c19-af5f-d1fd0a142b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c45c4cc3e6e6ffe23378ce0b4f26383369e92058
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391584"
---
# <a name="heapset"></a>_heapset
Zkontroluje haldách minimální konzistence a nastaví na zadanou hodnotou volné položky.  
  
> [!IMPORTANT]
>  Tato funkce je zastaralé. Od verze sady Visual Studio 2015, není k dispozici v CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _heapset(   
   unsigned int fill   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fill`  
 Zadejte znak.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_heapset` Vrátí jednu z následujících konstanty manifestu typu integer definované v Malloc.h.  
  
 `_HEAPBADBEGIN`  
 Počáteční záhlaví informace neplatná nebo nebyla nalezena.  
  
 `_HEAPBADNODE`  
 Kvůli poškození haldy nebo chybných uzlu byl nalezen.  
  
 `_HEAPEMPTY`  
 Halda nebyla inicializována.  
  
 `_HEAPOK`  
 Halda pravděpodobně konzistentní.  
  
 Kromě toho, pokud dojde k chybě `_heapset` nastaví `errno` k `ENOSYS`.  
  
## <a name="remarks"></a>Poznámky  
 `_heapset` Funkce zobrazuje umístění volné paměti nebo uzly, které byly neúmyslně přepsána.  
  
 `_heapset` kontroluje minimální konzistence v haldě a poté nastaví všech bajtů haldy volné položky k `fill` hodnotu. Tato hodnota známé ukazuje, která umístění paměti haldy obsahovat volné uzly a které obsahují data, která měla neúmyslně zapsána do uvolněné paměti. Pokud operační systém nepodporuje `_heapset`(například Windows 98), funkce vrátí hodnotu `_HEAPOK` a nastaví `errno` k `ENOSYS`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_heapset`|\<malloc.h >|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_heapset.c  
// This program checks the heap and  
// fills in free entries with the character 'Z'.  
  
#include <malloc.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int heapstatus;  
   char *buffer;  
  
   if( (buffer = malloc( 1 )) == NULL ) // Make sure heap is   
      exit( 0 );                        //    initialized       
   heapstatus = _heapset( 'Z' );        // Fill in free entries   
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf( "OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf( "OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
   free( buffer );  
}  
```  
  
```Output  
OK - heap is fine  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../c-runtime-library/memory-allocation.md)   
 [_heapadd –](../c-runtime-library/heapadd.md)   
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapmin –](../c-runtime-library/reference/heapmin.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)