---
title: "_memicmp –, _memicmp_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _memicmp_l
- _memicmp
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
- _memicmp
- memicmp_l
- _memicmp_l
dev_langs:
- C++
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b79c36bc665d1d7a32ef50984a75b48811985d1e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="memicmp-memicmpl"></a>_memicmp, _memicmp_l
Porovná dva vyrovnávací paměti (velká a malá písmena) znaků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _memicmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count   
);  
int _memicmp_l(  
   const void *buf1,  
   const void *buf2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buf1`  
 První vyrovnávací paměť.  
  
 `buf2`  
 Druhá vyrovnávací paměť.  
  
 `count`  
 Počet znaků.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje vztah mezi vyrovnávacími pamětmi.  
  
|Návratová hodnota|Vztah první počet bajtů buf1 a buf2|  
|------------------|--------------------------------------------------------|  
|< 0|`buf1` menší než `buf2`.|  
|0|`buf1` stejný jako `buf2`.|  
|> 0|`buf1` větší než `buf2`.|  
|`_NLSCMPERROR`|Došlo k chybě.|  
  
## <a name="remarks"></a>Poznámky  
 `_memicmp` Funkce Porovná první `count` znaky dvou vyrovnávacích pamětí `buf1` a `buf2` bajtů podle bajtů. Porovnání nerozlišuje malá a velká písmena.  
  
 Pokud má jedna `buf1` nebo `buf2` je ukazatel s hodnotou null, funkce vyvolá obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, funkce vrátí hodnotu `_NLSCMPERROR` a nastaví `errno` k `EINVAL`.  
  
 `_memicmp` používá aktuální národní prostředí pro chování závislých na národním prostředí; `_memicmp_l` se shoduje s tím rozdílem, že používá národní prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_memicmp`|\<Memory.h > nebo \<string.h >|  
|`_memicmp_l`|\<Memory.h > nebo \<string.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_memicmp.c  
// This program uses _memicmp to compare  
// the first 29 letters of the strings named first and  
// second without regard to the case of the letters.  
  
#include <memory.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   int result;  
   char first[] = "Those Who Will Not Learn from History";  
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";  
   // Note that the 29th character is right here ^  
  
   printf( "Compare '%.29s' to '%.29s'\n", first, second );  
   result = _memicmp( first, second, 29 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else if( result > 0 )  
      printf( "First is greater than second.\n" );  
}  
```  
  
```Output  
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'  
First is equal to second.  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp wmemcmp –](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset –, wmemset –](../../c-runtime-library/reference/memset-wmemset.md)   
 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)