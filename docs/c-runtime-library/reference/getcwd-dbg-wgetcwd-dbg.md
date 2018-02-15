---
title: "_getcwd_dbg –, _wgetcwd_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
dev_langs:
- C++
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc2538ce4e745917e23d67903b86677bacfbb979
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg
Ladicí verze [_getcwd –, _wgetcwd –](../../c-runtime-library/reference/getcwd-wgetcwd.md) funkce (dostupné pouze při ladění).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_getcwd_dbg(   
   char *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wgetcwd_dbg(   
   wchar_t *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro cestu.  
  
 `maxlen`  
 Maximální délka cesty ve znacích: `char` pro `_getcwd_dbg` a `wchar_t` pro `_wgetcwd_dbg`.  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na parametr `buffer`. Vrácená hodnota `NULL` označuje chybu a parametr `errno` je nastaven buď na hodnotu `ENOMEM` označující nedostatek paměti k přidělení `maxlen` bajtů (pokud je předána hodnota `NULL` parametru `buffer`), nebo na hodnotu `ERANGE` označující, že cesta je delší než `maxlen` znaků.  
  
 Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `_getcwd_dbg` a `_wgetcwd_dbg` funkce jsou stejné jako `_getcwd` a `_wgetcwd` s tím rozdílem, že když `_DEBUG` je definovaný, tyto funkce používají verzi ladění `malloc` a `_malloc_dbg` přidělit paměť, pokud `NULL` se předá jako první parametr. Další informace najdete v tématu [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat `_CRTDBG_MAP_ALLOC` příznak. Když `_CRTDBG_MAP_ALLOC` je definován, volání `_getcwd` a `_wgetcwd` jsou mapovány na `_getcwd_dbg` a `_wgetcwd_dbg`, s `blockType` nastavena na `_NORMAL_BLOCK`. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako `_CLIENT_BLOCK`. Další informace najdete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetcwd_dbg`|`_getcwd_dbg`|`_getcwd_dbg`|`_wgetcwd_dbg`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_getcwd_dbg`|\<crtdbg.h>|  
|`_wgetcwd_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [_getcwd, _wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [Ovládací prvek adresáře](../../c-runtime-library/directory-control.md)   
 [Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)