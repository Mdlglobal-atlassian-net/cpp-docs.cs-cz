---
title: "_fullpath_dbg –, _wfullpath_dbg – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
dev_langs: C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ca0d3229f539c05817fd9dddc4e8cd30ec5abdb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg
Verze [_fullpath –, _wfullpath –](../../c-runtime-library/reference/fullpath-wfullpath.md) , použijte ladicí verzi `malloc` přidělit paměť.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_fullpath_dbg(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wfullpath_dbg(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `absPath`  
 Ukazatel na vyrovnávací paměť obsahující název absolutní nebo úplné cesty, nebo `NULL`.  
  
 `relPath`  
 Relativní cesta.  
  
 `maxLength`  
 Maximální délka vyrovnávací paměť názvu absolutní cestu (`absPath`). Se délka v bajtech pro `_fullpath` , ale v široké znaky (`wchar_t`) pro `_wfullpath`.  
  
 `blockType`  
 Požadovaný typ bloku paměti: `_CLIENT_BLOCK` nebo `_NORMAL_BLOCK`.  
  
 `filename`  
 Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo `NULL`.  
  
 `linenumber`  
 Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo `NULL`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Jednotlivé funkce vrátí ukazatel do vyrovnávací paměti obsahující absolutní cesta (`absPath`). Pokud dojde k chybě (například pokud je předaná hodnota `relPath` zahrnuje písmeno jednotky, které není platná nebo nebyla nalezena, nebo pokud délka názvu vytvořený absolutní cestu (`absPath`) je větší než `maxLength`) funkce vrátí hodnotu `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 `_fullpath_dbg` a `_wfullpath_dbg` funkce jsou stejné jako `_fullpath` a `_wfullpath` s tím rozdílem, že když `_DEBUG` je definované, tyto funkce používají verzi ladění `malloc`, `_malloc_dbg`, přidělit paměť, pokud je hodnota NULL předat jako první parametr. Informace o ladění funkce `_malloc_dbg`, najdete v části [_malloc_dbg –](../../c-runtime-library/reference/malloc-dbg.md).  
  
 Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat `_CRTDBG_MAP_ALLOC` příznak. Když `_CRTDBG_MAP_ALLOC` je definován, volání `_fullpath` a `_wfullpath` jsou mapovány na `_fullpath_dbg` a `_wfullpath_dbg`, s `blockType` nastavena na `_NORMAL_BLOCK`. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako `_CLIENT_BLOCK`. Další informace najdete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath_dbg`|`_fullpath_dbg`|`_fullpath_dbg`|`_wfullpath_dbg`|  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fullpath_dbg`|\<crtdbg.h >|  
|`_wfullpath_dbg`|\<crtdbg.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_fullpath –, _wfullpath –](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)