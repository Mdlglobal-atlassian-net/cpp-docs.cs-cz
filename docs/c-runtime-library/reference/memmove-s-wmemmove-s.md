---
title: "memmove_s –, wmemmove_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
dev_langs: C++
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8194acf1a8a0708d2584745a7a49449ca7f554c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s
Přesune na jiný jednu vyrovnávací paměti. Toto jsou verze [memmove –, wmemmove –](../../c-runtime-library/reference/memmove-wmemmove.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      errno_t memmove_s(  
   void *dest,  
   size_t numberOfElements,  
   const void *src,  
   size_t count  
);  
errno_t wmemmove_s(  
   wchar_t *dest,  
   size_t numberOfElements,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Cílový objekt.  
  
 `numberOfElements`  
 Velikost cílové vyrovnávací paměti.  
  
 `src`  
 Zdrojový objekt.  
  
 `count`  
 Počet bajtů (`memmove_s`) nebo znaky (`wmemmove_s`) ke kopírování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`dest`|`numberOfElements`|`src`|Návratová hodnota|Obsah`dest`|  
|------------|------------------------|-----------|------------------|------------------------|  
|`NULL`|všechny|všechny|`EINVAL`|nedojde ke změně|  
|všechny|všechny|`NULL`|`EINVAL`|nedojde ke změně|  
|všechny|< `count`|všechny|`ERANGE`|nedojde ke změně|  
  
## <a name="remarks"></a>Poznámky  
 Kopie `count` bajtů znaky z `src` k `dest`. Pokud se některé oblasti oblasti zdroj a cíl překrývají, `memmove_s` zajistí, že původní zdrojový bajtů v překrývající se oblasti zkopírovaly před přepsáním.  
  
 Pokud `dest` nebo, pokud `src` je ukazatel s hodnotou null, nebo pokud cílový řetězec je příliš malá, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EINVAL` a nastavte `errno` k `EINVAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`memmove_s`|\<String.h >|  
|`wmemmove_s`|\<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_memmove_s.c  
//  
// The program demonstrates the   
// memmove_s function which works as expected  
// for moving overlapping regions.  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   char str[] = "0123456789";  
  
   printf("Before: %s\n", str);  
  
   // Move six bytes from the start of the string  
   // to a new position shifted by one byte. To protect against  
   // buffer overrun, the secure version of memmove requires the  
   // the length of the destination string to be specified.   
  
   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);   
  
   printf_s(" After: %s\n", str);  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
Before: 0123456789  
 After: 0012345789  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy –](../../c-runtime-library/reference/memccpy.md)   
 [memcpy wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy_s – wcscpy_s –, _mbscpy_s –](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)