---
title: "_strdup_dbg –, _wcsdup_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strdup_dbg
- _wcsdup_dbg
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
- _wcsdup_dbg
- strdup_dbg
- _strdup_dbg
- wcsdup_dbg
dev_langs:
- C++
helpviewer_keywords:
- _wcsdup_dbg function
- stdup_dbg function
- copying strings
- duplicating strings
- strings [C++], copying
- strings [C++], duplicating
- _strdup_dbg function
- wcsdup_dbg function
ms.assetid: 681db70c-d124-43ab-b83e-5eeea9035097
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7865335eb5b483ca722e06c31b935751c92c80bd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strdupdbg-wcsdupdbg"></a>_strdup_dbg, _wcsdup_dbg
Verze [_strdup – a _wcsdup –](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md) , použijte ladicí verzi `malloc`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_strdup_dbg(  
   const char *strSource,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wcsdup_dbg(  
   const wchar_t *strSource,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `strSource`  
 Řetězce ukončené hodnotou Null zdroje.  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo hodnota NULL.  
  
 `linenumber`  
 Číslo ve zdrojovém souboru, kde byla vyžádána operace přidělení řádku nebo hodnota NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na umístění úložiště pro řetězec zkopírovaný nebo `NULL` Pokud nelze přidělit úložiště.  
  
## <a name="remarks"></a>Poznámky  
 `_strdup_dbg` a `_wcsdup_dbg` funkce jsou stejné jako `_strdup` a `_wcsdup` s tím rozdílem, že když `_DEBUG` je definované, tyto funkce používají verzi ladění `malloc`, `_malloc_dbg`, přidělit paměť pro duplicitní řetězce. Informace o ladění funkce `_malloc_dbg`, najdete v části [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat příznak `_CRTDBG_MAP_ALLOC`. Když `_CRTDBG_MAP_ALLOC` je definován, volání `_strdup` a `_wcsdup` jsou mapovány na `_strdup_dbg` a `_wcsdup_dbg`, s `blockType` nastavena na `_NORMAL_BLOCK`. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako `_CLIENT_BLOCK`. Další informace o typech bloku, najdete v části [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsdup_dbg`|`_strdup_dbg`|`_mbsdup`|`_wcsdup_dbg`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_strdup_dbg`, `_wcsdup_dbg`|\<crtdbg.h>|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="libraries"></a>Knihovny  
 Všechny ladicí verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [_strdup, _wcsdup, _mbsdup](../../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)   
 [Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)