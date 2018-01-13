---
title: "_heapchk – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapchk
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
- _heapchk
- heapchk
dev_langs: C++
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 790d887009137ccc9115484b2ace57302c94d851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="heapchk"></a>_heapchk
Spustí kontrolu konzistence na haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _heapchk( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `_heapchk`Vrátí jednu z následujících konstanty manifestu typu integer definované v Malloc.h.  
  
 `_HEAPBADBEGIN`  
 Informace počáteční hlavičky je chybný nebo nebyl nalezen.  
  
 `_HEAPBADNODE`  
 Chybný uzel nebyl nalezen nebo je poškozena halda.  
  
 `_HEAPBADPTR`  
 Ukazatel do haldy není platný.  
  
 `_HEAPEMPTY`  
 Halda nebyla inicializována.  
  
 `_HEAPOK`  
 Halda pravděpodobně konzistentní.  
  
 Kromě toho, pokud dojde k chybě `_heapchk` nastaví `errno` k `ENOSYS`.  
  
## <a name="remarks"></a>Poznámky  
 `_heapchk` Funkce pomáhá ladění problémy související s kontrolou konzistence minimální haldy. Pokud operační systém nepodporuje `_heapchk`(například Windows 98), funkce vrátí hodnotu `_HEAPOK` a nastaví `errno` k `ENOSYS`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_heapchk`|\<malloc.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_heapchk.c  
// This program checks the heap for  
// consistency and prints an appropriate message.  
  
#include <malloc.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  heapstatus;  
   char *buffer;  
  
   // Allocate and deallocate some memory  
   if( (buffer = (char *)malloc( 100 )) != NULL )  
      free( buffer );  
  
   // Check heap status  
   heapstatus = _heapchk();  
   switch( heapstatus )  
   {  
   case _HEAPOK:  
      printf(" OK - heap is fine\n" );  
      break;  
   case _HEAPEMPTY:  
      printf(" OK - heap is empty\n" );  
      break;  
   case _HEAPBADBEGIN:  
      printf( "ERROR - bad start of heap\n" );  
      break;  
   case _HEAPBADNODE:  
      printf( "ERROR - bad node in heap\n" );  
      break;  
   }  
}  
```  
  
```Output  
OK - heap is fine  
```  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [_heapadd –](../../c-runtime-library/heapadd.md)   
 [_heapmin –](../../c-runtime-library/reference/heapmin.md)   
 [_heapset –](../../c-runtime-library/heapset.md)   
 [_heapwalk](../../c-runtime-library/reference/heapwalk.md)