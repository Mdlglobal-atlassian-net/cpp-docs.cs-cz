---
title: "memcpy_s –, wmemcpy_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memcpy_s
- wmemcpy_s
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
- wmemcpy_s
- memcpy_s
dev_langs: C++
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ac0b4cd7783cd41d480777fe8116a0facea58a28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="memcpys-wmemcpys"></a>memcpy_s, wmemcpy_s
Počet bajtů kopie mezi vyrovnávací paměti. Toto jsou verze [memcpy wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t memcpy_s(  
   void *dest,  
   size_t destSize,  
   const void *src,  
   size_t count   
);  
errno_t wmemcpy_s(  
   wchar_t *dest,  
   size_t destSize,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Vyrovnávací paměť nového.  
  
 `destSize`  
 Cílová vyrovnávací paměť v bajtech pro memcpy_s – a široké znaky (wchar_t) pro wmemcpy_s – velikost.  
  
 `src`  
 Zkopírovat z vyrovnávací paměti.  
  
 `count`  
 Počet znaků pro kopírování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěšného; Kód chyby při selhání.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`dest`|`destSize`|`src`|`count`|Návratová hodnota|Obsah`dest`|  
|------------|----------------|-----------|---|------------------|------------------------|  
|všechny|všechny|všechny|0|0|nedojde ke změně|  
|`NULL`|všechny|všechny|nulová|`EINVAL`|nedojde ke změně|  
|všechny|všechny|`NULL`|nulová|`EINVAL`|`dest`je dojde k vynulování|  
|všechny|< `count`|všechny|nulová|`ERANGE`|`dest`je dojde k vynulování|  
  
## <a name="remarks"></a>Poznámky  
 `memcpy_s`kopie `count` bajtů z `src` k `dest`; `wmemcpy_s` kopie `count` široké znaky (dva bajty). Pokud zdrojové a cílové překrývají, chování `memcpy_s` není definován. Použití `memmove_s` pro zpracování překrývající se oblasti.  
  
 Tyto funkce ověřit jejich parametrů. Pokud `count` je nulová a `dest` nebo `src` je ukazatel s hodnotou null, nebo `destSize` je menší než `count`, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `EINVAL` nebo `ERANGE` a nastavte `errno` na návratovou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`memcpy_s`|\<Memory.h > nebo \<string.h >|  
|`wmemcpy_s`|\<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_memcpy_s.c  
// Copy memory in a more secure way.  
  
#include <memory.h>  
#include <stdio.h>  
  
int main()  
{  
   int a1[10], a2[100], i;  
   errno_t err;  
  
   // Populate a2 with squares of integers  
   for (i = 0; i < 100; i++)  
   {  
      a2[i] = i*i;  
   }  
  
   // Tell memcpy_s to copy 10 ints (40 bytes), giving  
   // the size of the a1 array (also 40 bytes).  
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );      
   if (err)  
   {  
      printf("Error executing memcpy_s.\n");  
   }  
   else  
   {  
     for (i = 0; i < 10; i++)  
       printf("%d ", a1[i]);  
   }  
   printf("\n");  
}  
```  
  
```Output  
0 1 4 9 16 25 36 49 64 81   
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy –](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr –](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp wmemcmp –](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove –, wmemmove –](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset –, wmemset –](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy –, _strncpy_l –, wcsncpy –, _wcsncpy_l –, _mbsncpy –, _mbsncpy_l –](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strncpy_s –, _strncpy_s_l –, wcsncpy_s –, _wcsncpy_s_l –, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)