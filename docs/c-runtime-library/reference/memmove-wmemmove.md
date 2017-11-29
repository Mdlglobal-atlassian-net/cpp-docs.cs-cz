---
title: "memmove –, wmemmove – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
dev_langs: C++
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b907524992b1fee2696856fe13cfc983fdfb8c61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove
Přesune na jiný jednu vyrovnávací paměti. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [memmove_s –, wmemmove_s –](../../c-runtime-library/reference/memmove-s-wmemmove-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *memmove(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemmove(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Cílový objekt.  
  
 `src`  
 Zdrojový objekt.  
  
 `count`  
 Počet bajtů (`memmove`) nebo znaky (`wmemmove`) ke kopírování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota `dest`.  
  
## <a name="remarks"></a>Poznámky  
 Kopie `count` bajtů (`memmove`) nebo znaky (`wmemmove`) z `src` k `dest`. Pokud některé oblasti oblasti zdroj a cíl překrývají, obě funkce Ujistěte se, že původní zdrojový bajtů v překrývající se oblasti jsou kopírovány před přepsáním.  
  
 **Poznámka k zabezpečení** Ujistěte se, že cílová vyrovnávací paměť je stejný, velké nebo větší než zdrojová vyrovnávací paměť. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 `memmove` a `wmemmove` funkce bude zastaralá pouze pokud konstanta `_CRT_SECURE_DEPRECATE_MEMORY` je definovaná před příkazem zahrnutí v pořadí pro funkcí, které mají být zastaralé, například v následujícím příkladu:  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <string.h>  
or  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`memmove`|\<String.h >|  
|`wmemmove`|\<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_memcpy.c  
// Illustrate overlapping copy: memmove  
// always handles it correctly; memcpy may handle  
// it correctly.  
//  
  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
  
char str1[7] = "aabbcc";  
  
int main( void )  
{  
   printf( "The string: %s\n", str1 );  
   memcpy( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
  
   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string  
  
   printf( "The string: %s\n", str1 );  
   memmove( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
}  
```  
  
```Output  
The string: aabbcc  
New string: aaaabb  
The string: aabbcc  
New string: aaaabb  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy –](../../c-runtime-library/reference/memccpy.md)   
 [memcpy wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy –, _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l –](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)