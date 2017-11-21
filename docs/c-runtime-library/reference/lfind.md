---
title: "_lfind – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lfind
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lfind
- _lfind
dev_langs: C++
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f883aa9f17c8272335a91ebf333e050888be8257
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lfind"></a>_lfind
Provede lineárního hledání pro zadaný klíč. Bezpečnější verze této funkce je k dispozici. v tématu [_lfind_s –](../../c-runtime-library/reference/lfind-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_lfind(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Objekt, který chcete vyhledat.  
  
 `base`  
 Ukazatel na základní dat hledání.  
  
 `num`  
 Počet prvků pole.  
  
 `width`  
 Šířka prvků pole.  
  
 `compare`  
 Ukazatel na rutiny porovnání. První parametr je ukazatel na klíč pro vyhledávání. Druhý parametr je ukazatel na element pole, který se má porovnat s klíčem.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je nalezen klíč, `_lfind` vrací ukazatel na element pole v `base` odpovídající `key`. Pokud není nalezen klíč, `_lfind` vrátí `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 `_lfind` Funkce provádí lineárního hledání pro hodnotu `key` v pole `num` elementy, každý z `width` bajtů. Na rozdíl od `bsearch`, `_lfind` nevyžaduje pole, která se má seřadit. `base` Argument je ukazatel na základní pole má proběhnout. `compare` Argument je ukazatel na rutiny zadanou uživatelem, který porovná dva elementy pole a vrátí hodnotu udávající, jejich vztahu. `_lfind`volání `compare` rutiny jeden či více krát během hledání, předávání ukazatele na dva elementy pole při každém volání. `compare` Rutinu musí porovnat elementy a pak se vraťte nenulové hodnoty (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).  
  
 Tato funkce ověří jeho parametry. Pokud `compare`, `key` nebo `num` je `NULL`, nebo pokud `base` má hodnotu NULL a *`num` je nenulové hodnoty, nebo pokud `width` je menší než nula, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_lfind`|\<Search.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_lfind.c  
// This program uses _lfind to search a string array  
// for an occurrence of "hello".  
  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
  
int main( )  
{  
   char *arr[] = {"Hi", "Hello", "Bye"};  
   int n = sizeof(arr) / sizeof(char*);  
   char **result;  
   char *key = "hello";  
  
   result = (char **)_lfind( &key, arr,   
                      &n, sizeof(char *), compare );  
  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "hello not found!\n" );  
}  
```  
  
```Output  
Hello found  
```  
  
## <a name="see-also"></a>Viz také  
 [Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind_s –](../../c-runtime-library/reference/lfind-s.md)   
 [bsearch –](../../c-runtime-library/reference/bsearch.md)   
 [_lsearch –](../../c-runtime-library/reference/lsearch.md)   
 [qsort –](../../c-runtime-library/reference/qsort.md)