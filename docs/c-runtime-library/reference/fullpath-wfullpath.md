---
title: "_fullpath –, _wfullpath – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
dev_langs: C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a1cc6a80609828d084b56ef4f981c9d03de8070
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath
Vytvoří název absolutní nebo úplnou cestu pro zadaný relativní cesta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_fullpath(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength   
);  
wchar_t *_wfullpath(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `absPath`  
 Ukazatel na absolutní nebo úplnou cestu obsahující název nebo hodnota NULL.  
  
 `relPath`  
 Relativní cesta.  
  
 `maxLength`  
 Maximální délka vyrovnávací paměť názvu absolutní cestu (`absPath`). Se délka v bajtech pro `_fullpath` , ale v široké znaky (`wchar_t`) pro `_wfullpath`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na vyrovnávací paměť obsahující absolutní cesta (`absPath`). Pokud dojde k chybě (například pokud je předaná hodnota `relPath` zahrnuje písmeno jednotky, které není platná nebo nebyla nalezena, nebo pokud délka názvu vytvořený absolutní cestu (`absPath`) je větší než `maxLength`), funkce vrátí hodnotu `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 `_fullpath` Funkce rozšíří názvem relativní cesty v `relPath` jeho plně kvalifikovanou nebo absolutní cesta a ukládá tento název v `absPath`. Pokud `absPath` má hodnotu NULL, `malloc` se používá k přidělení vyrovnávací paměti dostatečně dlouhé, aby udržení název cesty. Je zodpovědností volajícího, aby bez této vyrovnávací paměti. Relativní cesta Určuje cestu do jiného umístění z aktuálního umístění (například aktuální pracovní adresář: "."). Název absolutní cesta je rozšíření relativní cesta název, který stavy celou cestu potřebné k dosažení požadované umístění z kořenového adresáře systému souborů. Na rozdíl od `_makepath`, `_fullpath` lze použít k získání názvu absolutní cesta relativní cesty (`relPath`), zahrnují ". /"nebo".. nebo "v jejich názvy.  
  
 Pokud chcete používat C běhové rutiny, například žádost musí obsahovat soubory hlaviček, které obsahují deklarace pro rutiny. Každý soubor hlaviček patří příkaz odkazy na umístění souboru relativní způsobem (z pracovní adresář aplikace):  
  
```  
#include <stdlib.h>  
```  
  
 Když může být absolutní cesta k souboru (skutečné umístění systému souborů):  
  
```  
\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h  
```  
  
 `_fullpath`automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle vícebajtové znakové stránky aktuálně používán. `_wfullpath`široká charakterová verze `_fullpath`; argumenty řetězce, které mají `_wfullpath` jsou široká charakterová řetězce. `_wfullpath`a `_fullpath` vyjma toho, že se chovají stejně jako `_wfullpath` nezpracovává řetězců vícebajtových znaků.  
  
 Pokud `_DEBUG` a `_CRTDBG_MAP_ALLOC` jsou obě definovány, volání `_fullpath` a `_wfullpath` jsou nahrazovány volání `_fullpath_dbg` a `_wfullpath_dbg` umožňující ladění přidělení paměti. Další informace najdete v tématu [_fullpath_dbg –, _wfullpath_dbg –](../../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md).  
  
 Tato funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md), pokud `maxlen` je menší než nebo rovna 0. Pokud je povoleno spuštění pokračovat, tato funkce nastaví `errno` k `EINVAL` a vrátí `NULL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath`|`_fullpath`|`_fullpath`|`_wfullpath`|  
  
 Pokud `absPath` vyrovnávací paměť je `NULL`, `_fullpath` volání [malloc –](../../c-runtime-library/reference/malloc.md) přidělit vyrovnávací paměť a ignoruje `maxLength` argument. Je zodpovědností má volající se zrušit přidělení této vyrovnávací paměti (pomocí [volné](../../c-runtime-library/reference/free.md)) podle potřeby. Pokud `relPath` argument určuje diskovou jednotku, aktuální adresář této jednotky je v kombinaci s cestou.  
  
## <a name="requirements"></a>Požadavky  
  
|Funkce|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_fullpath`|\<stdlib.h >|  
|`_wfullpath`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_fullpath.c  
// This program demonstrates how _fullpath  
// creates a full path from a partial path.  
  
#include <stdio.h>  
#include <conio.h>  
#include <stdlib.h>  
#include <direct.h>  
  
void PrintFullPath( char * partialPath )  
{  
   char full[_MAX_PATH];  
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )  
      printf( "Full path is: %s\n", full );  
   else  
      printf( "Invalid path\n" );  
}  
  
int main( void )  
{  
   PrintFullPath( "test" );  
   PrintFullPath( "\\test" );  
   PrintFullPath( "..\\test" );  
}  
```  
  
```Output  
Full path is: C:\Documents and Settings\user\My Documents\test  
Full path is: C:\test  
Full path is: C:\Documents and Settings\user\test  
```  
  
## <a name="see-also"></a>Viz také  
 [Zpracování souborů](../../c-runtime-library/file-handling.md)   
 [_getcwd –, _wgetcwd –](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [_getdcwd –, _wgetdcwd –](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [_makepath –, _wmakepath –](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_splitpath –, _wsplitpath –](../../c-runtime-library/reference/splitpath-wsplitpath.md)