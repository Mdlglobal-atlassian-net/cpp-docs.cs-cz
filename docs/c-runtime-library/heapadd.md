---
title: _heapadd – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _heapadd
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- heapadd
- _heapadd
dev_langs:
- C++
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1f212bdbf8ee617a1cfb6647627bc0c881b49be
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="heapadd"></a>_heapadd
Přidá do halda paměti.  
  
> [!IMPORTANT]
>  Tato funkce je zastaralé. Od verze sady Visual Studio 2015, není k dispozici v CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _heapadd(   
   void *memblock,  
   size_t size   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `memblock`  
 Ukazatel na paměť haldy.  
  
 `size`  
 Velikost paměti, které chcete přidat, v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `_heapadd` vrátí hodnotu 0; jinak hodnota, funkce vrátí hodnotu -1 a nastaví `errno` k `ENOSYS`.  
  
 Další informace o tomto a ostatní návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 Od verze Visual C++ verze 4.0, podkladová struktura haldy byla přesunuta do běhové knihovny jazyka C pro podporu nových funkcí ladění. V důsledku toho `_heapadd` již není podporována na jakékoli platformě, která je založená na volání rozhraní API Win32.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_heapadd`|\<malloc.h >|\<errno.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../c-runtime-library/memory-allocation.md)   
 [Volné](../c-runtime-library/reference/free.md)   
 [_heapchk](../c-runtime-library/reference/heapchk.md)   
 [_heapmin –](../c-runtime-library/reference/heapmin.md)   
 [_heapset –](../c-runtime-library/heapset.md)   
 [_heapwalk](../c-runtime-library/reference/heapwalk.md)   
 [malloc –](../c-runtime-library/reference/malloc.md)   
 [realloc](../c-runtime-library/reference/realloc.md)