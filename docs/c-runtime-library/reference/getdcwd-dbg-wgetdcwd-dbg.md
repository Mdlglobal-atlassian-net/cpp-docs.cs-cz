---
title: "_getdcwd_dbg –, _wgetdcwd_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 788ef0f0b745132c4b8d270129d8a182a2774361
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg, _wgetdcwd_dbg
Ladicí verze [_getdcwd –, _wgetdcwd –](../../c-runtime-library/reference/getdcwd-wgetdcwd.md) funkce (dostupné pouze při ladění).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_getdcwd_dbg(  
   int drive,  
   char *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wgetdcwd_dbg(  
   int drive,  
   wchar_t *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `drive`  
 Název na disk.  
  
 `buffer`  
 Umístění úložiště pro cestu.  
  
 `maxlen`  
 Maximální délka cesty ve znacích: `char` pro `_getdcwd_dbg` a `wchar_t` pro `_wgetdcwd_dbg`.  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na parametr `buffer`. Vrácená hodnota `NULL` označuje chybu a parametr `errno` je nastaven buď na hodnotu `ENOMEM` označující nedostatek paměti k přidělení `maxlen` bajtů (pokud je předána hodnota `NULL` parametru `buffer`), nebo na hodnotu `ERANGE` označující, že cesta je delší než `maxlen` znaků. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_getdcwd_dbg` a `_wgetdcwd_dbg` funkce jsou stejné jako `_getdcwd` a `_wgetdcwd` s tím rozdílem, že když `_DEBUG` je definovaný, tyto funkce používají verzi ladění `malloc` a `_malloc_dbg` přidělit paměť, pokud `NULL` se předá jako `buffer` parametr. Další informace najdete v tématu [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat `_CRTDBG_MAP_ALLOC` příznak. Když `_CRTDBG_MAP_ALLOC` je definován, volání `_getdcwd` a `_wgetdcwd` jsou mapovány na `_getdcwd_dbg` a `_wgetdcwd_dbg`, s `blockType` nastavena na `_NORMAL_BLOCK`. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako `_CLIENT_BLOCK`. Další informace najdete v tématu [typy bloky v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetdcwd_dbg`|`_getdcwd_dbg`|`_getdcwd_dbg`|`_wgetdcwd_dbg`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_getdcwd_dbg`|\<crtdbg.h>|  
|`_wgetdcwd_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [_getdcwd, _wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)