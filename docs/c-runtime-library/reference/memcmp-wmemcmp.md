---
title: "memcmp wmemcmp – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- memcmp
- wmemcmp
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
- memcmp
- wmemcmp
dev_langs: C++
helpviewer_keywords:
- wmemcmp function
- memcmp function
ms.assetid: 0c21c3e3-8ee4-40e5-add1-eb26d225fd8d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 423334c3300d0218eb76df8f90a2eb30ea8cc369
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="memcmp-wmemcmp"></a>memcmp, wmemcmp
Porovná znaky ve dvou vyrovnávacích pamětech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int memcmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count  
);  
int wmemcmp(  
   const wchar_t * buf1,  
   const wchar_t * buf2,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buf1`  
 První vyrovnávací paměť.  
  
 `buf2`  
 Druhá vyrovnávací paměť.  
  
 `count`  
 Počet znaků, které mají být porovnány. (Bajty porovná funkce `memcmp`, široké znaky porovná funkce `wmemcmp`).  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota označuje vztah mezi vyrovnávacími pamětmi.  
  
|Návratová hodnota|Vztah prvních znaků `count` proměnných buf1 a buf2|  
|------------------|---------------------------------------------------------------|  
|< 0|`buf1`menší než`buf2`|  
|0|`buf1`stejný jako`buf2`|  
|> 0|`buf1`větší než`buf2`|  
  
## <a name="remarks"></a>Poznámky  
 Porovná počet znaků podle proměnné `count` v proměnných `buf1` a `buf2` a vrátí hodnotu, která určuje jejich vzájemný vztah. Znaménko nenulové návratové hodnoty je znamení rozdílu mezi prvním párem různých hodnot ve vyrovnávacích pamětech. Tyto hodnoty jsou interpretovány jako typ `unsigned char` pro funkci `memcmp` a jako typ `wchar_t` pro funkci `wmemcmp`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`memcmp`|\<Memory.h > nebo \<string.h >|  
|`wmemcmp`|\<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_memcmp.c  
/* This program uses memcmp to compare  
 * the strings named first and second. If the first  
 * 19 bytes of the strings are equal, the program  
 * considers the strings to be equal.  
 */  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char first[]  = "12345678901234567890";  
   char second[] = "12345678901234567891";  
   int int_arr1[] = {1,2,3,4};  
   int int_arr2[] = {1,2,3,4};  
   int result;  
  
   printf( "Compare '%.19s' to '%.19s':\n", first, second );  
   result = memcmp( first, second, 19 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else  
      printf( "First is greater than second.\n" );  
  
   printf( "Compare '%d,%d' to '%d,%d':\n", int_arr1[0], int_arr1[1], int_arr2[0], int_arr2[1]);  
   result = memcmp( int_arr1, int_arr2, sizeof(int) * 2 );  
   if( result < 0 )  
      printf( "int_arr1 is less than int_arr2.\n" );  
   else if( result == 0 )  
      printf( "int_arr1 is equal to int_arr2.\n" );  
   else   
      printf( "int_arr1 is greater than int_arr2.\n" );  
}  
```  
  
```Output  
Compare '1234567890123456789' to '1234567890123456789':  
First is equal to second.  
Compare '1,2' to '1,2':  
int_arr1 is equal to int_arr2.  
```  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy –](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr –](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcpy wmemcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset –, wmemset –](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcmp – wcscmp –, _mbscmp –](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp –, wcsncmp –, _mbsncmp –, _mbsncmp_l –](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)