---
title: "_heapmin – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _heapmin
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
- _heapmin
- heapmin
dev_langs: C++
helpviewer_keywords:
- heap memory
- minimizing heaps
- memory, releasing
- heaps, releasing unused memory
- _heapmin function
- heapmin function
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1318e8d18ddeb5031efdf3066f9fa3020c8e9afd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="heapmin"></a>_heapmin
Uvolní paměť nepoužívané haldy v operačním systému.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _heapmin( void );  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného `_heapmin` vrátí hodnotu 0; jinak hodnota, funkce vrátí hodnotu -1 a nastaví `errno` k `ENOSYS`.  
  
 Další informace o tomto a ostatní návratové kódy najdete v tématu [_doserrno – kód chyby, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_heapmin` Funkce minimalizuje halda uvolněním nepoužívané halda paměti operačního systému. Pokud operační systém nepodporuje `_heapmin`(například Windows 98), funkce vrátí hodnotu -1 a nastaví `errno` k `ENOSYS`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_heapmin`|\<malloc.h >|\<errno.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Přidělení paměti](../../c-runtime-library/memory-allocation.md)   
 [Uvolněte](../../c-runtime-library/reference/free.md)   
 [_heapadd –](../../c-runtime-library/heapadd.md)   
 [_heapchk –](../../c-runtime-library/reference/heapchk.md)   
 [_heapset –](../../c-runtime-library/heapset.md)   
 [_heapwalk –](../../c-runtime-library/reference/heapwalk.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)