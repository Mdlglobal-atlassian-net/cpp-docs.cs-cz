---
title: "_dupenv_s_dbg –, _wdupenv_s_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
dev_langs: C++
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72412790fc7bd71d25d0a77fdb0ede8d7b9e31a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg, _wdupenv_s_dbg
Získání hodnoty z aktuální prostředí.  Verze [_dupenv_s –, _wdupenv_s –](../../c-runtime-library/reference/dupenv-s-wdupenv-s.md) , přidělit paměť s [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md) poskytnout další informace o ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _dupenv_s_dbg(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
errno_t _wdupenv_s_dbg(  
   wchar_t **buffer,  
   size_t * numberOfElements,  
   const wchar_t *varname,  
   int blockType,  
   const char *filename,  
   int linenumber  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Vyrovnávací paměť pro uložení hodnota proměnné.  
  
 `numberOfElements`  
 Velikost `buffer`.  
  
 `varname`  
 Název proměnné prostředí.  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor nebo `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, kód chyby při selhání.  
  
 Tyto funkce ověřit jejich parametrů; Pokud `buffer` nebo `varname` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, nastavte funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
 Pokud tyto funkce nemůže přidělit dostatek paměti, nastavují `buffer` k `NULL` a `numberOfElements` 0, a vrátí `ENOMEM`.  
  
## <a name="remarks"></a>Poznámky  
 `_dupenv_s_dbg` a `_wdupenv_s_dbg` funkce jsou stejné jako `_dupenv_s` a `_wdupenv_s` s tím rozdílem, že když `_DEBUG` je definovaný, tyto funkce používají verzi ladění [malloc –](../../c-runtime-library/reference/malloc.md), [_ malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md), přidělit paměť pro hodnotu proměnné prostředí. Informace o ladění funkce `_malloc_dbg`, najdete v části [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat příznak `_CRTDBG_MAP_ALLOC`. Když `_CRTDBG_MAP_ALLOC` je definován, volání `_dupenv_s` a `_wdupenv_s` jsou mapovány na `_dupenv_s_dbg` a `_wdupenv_s_dbg`, s `blockType` nastavena na `_NORMAL_BLOCK`. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako `_CLIENT_BLOCK`. Další informace o typech bloku, najdete v části [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s_dbg`|`_dupenv_s_dbg`|`_dupenv_s_dbg`|`_wdupenv_s_dbg`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_dupenv_s_dbg`|\<crtdbg.h >|  
|`_wdupenv_s_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_dupenv_s_dbg.c  
#include  <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",  
      _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [Konstanty prostředí](../../c-runtime-library/environmental-constants.md)   
 [getenv_s –, _wgetenv_s –](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s –, _wputenv_s –](../../c-runtime-library/reference/putenv-s-wputenv-s.md)