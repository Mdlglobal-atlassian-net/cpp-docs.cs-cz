---
title: "_tempnam_dbg –, _wtempnam_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtempnam_dbg
- _tempnam_dbg
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
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
dev_langs: C++
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d1c4013dcfcbc6049957978316398566c60089b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg, _wtempnam_dbg
Funkce verze [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) , použijte ladicí verzi `malloc, _malloc_dbg`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_tempnam_dbg(  
   const char *dir,  
   const char *prefix,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wtempnam_dbg(  
   const wchar_t *dir,  
   const wchar_t *prefix,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dir`  
 Cesty použité v názvu souboru, pokud neexistuje žádná proměnná prostředí TMP, nebo pokud TMP není platný adresář.  
  
 `prefix`  
 Řetězec, který bude pre čekajícího na názvy vrácený `_tempnam`.  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivé funkce vrací ukazatel na název vygenerovaný nebo `NULL` Pokud dojde k selhání. Selhání může dojít, pokud je zadán neplatný adresář název proměnné prostředí TMP a v `dir` parametr.  
  
> [!NOTE]
>  `free`(nebo `free_dbg`) potřebuje volat pro ukazatele přidělené `_tempnam_dbg` a `_wtempnam_dbg`.  
  
## <a name="remarks"></a>Poznámky  
 `_tempnam_dbg` a `_wtempnam_dbg` funkce jsou stejné jako `_tempnam` a `_wtempnam` s tím rozdílem, že když `_DEBUG` je definovaný, tyto funkce používají verzi ladění `malloc` a `_malloc_dbg`, přidělit paměť, pokud `NULL` se předá jako první parametr. Další informace najdete v tématu [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat příznak `_CRTDBG_MAP_ALLOC`. Když `_CRTDBG_MAP_ALLOC` je definován, volání `_tempnam` a `_wtempnam` jsou mapovány na `_tempnam_dbg` a `_wtempnam_dbg`, s `blockType` nastavena na `_NORMAL_BLOCK`. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako `_CLIENT_BLOCK`. Další informace najdete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttempnam_dbg`|`_tempnam_dbg`|`_tempnam_dbg`|`_wtempnam_dbg`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_tempnam_dbg`, `_wtempnam_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [_tempnam –, _wtempnam –, tmpnam –, _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)