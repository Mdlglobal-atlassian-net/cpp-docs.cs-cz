---
title: "_lsearch – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lsearch
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
- _lsearch
- lsearch
dev_langs: C++
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ffb2c0ec3547278f048855bb72a2e4ae1bb00287
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lsearch"></a>_lsearch
Provede lineárního hledání pro hodnotu; Přidá na konec seznamu, pokud není nalezen. Bezpečnější verze této funkce je k dispozici. v tématu [_lsearch_s –](../../c-runtime-library/reference/lsearch-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_lsearch(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   unsigned int width,  
   int (__cdecl *compare)(const void *, const void *)   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Objekt, který chcete vyhledat.  
  
 `base`  
 Ukazatel na základní pole má proběhnout.  
  
 `num`  
 Počet elementů.  
  
 `width`  
 Šířka každého pole elementu.  
  
 `compare`  
 Ukazatel na rutiny porovnání. První parametr je ukazatel na klíč pro vyhledávání. Druhý parametr je ukazatel na element pole, který se má porovnat s klíčem.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je nalezen klíč, `_lsearch` vrací ukazatel na element pole v `base` odpovídající `key`. Pokud není nalezen klíč, `_lsearch` vrací ukazatel na nově přidané položky na konci tohoto pole.  
  
## <a name="remarks"></a>Poznámky  
 `_lsearch` Funkce provádí lineárního hledání pro hodnotu `key` v pole `num` elementy, každý z `width` bajtů. Na rozdíl od `bsearch`, `_lsearch` nevyžaduje pole, která se má seřadit. Pokud `key` není nalezen, `_lsearch` přidá na konec pole a zvýší `num`.  
  
 `compare` Argument je ukazatel na rutiny zadanou uživatelem, který porovnává dva elementy pole a vrátí hodnotu udávající, jejich vztahu. `_lsearch`volání `compare` rutiny jeden či více krát během hledání, předávání ukazatele na dva elementy pole při každém volání. `compare`musí porovnat elementy a vrátit buď nenulové hodnoty (tj. elementy se liší), nebo 0 (tj. elementy jsou identické).  
  
 Tato funkce ověří jeho parametry. Pokud `compare`, `key` nebo `num` je `NULL`, nebo pokud `base` má hodnotu NULL a *`num` je nenulové hodnoty, nebo pokud `width` je menší než nula, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_lsearch`|\<Search.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_lsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( const void *arg1, const void *arg2 );  
  
int main(void)  
{  
   char * wordlist[4] = { "hello", "thanks", "bye" };  
                            // leave room to grow...  
   int n = 3;  
   char **result;  
   char *key = "extra";  
   int i;  
  
   printf( "wordlist before _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
  
   result = (char **)_lsearch( &key, wordlist,   
                      &n, sizeof(char *), compare );  
  
   printf( "wordlist after _lsearch:" );  
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );  
   printf( "\n" );  
}  
  
int compare(const void *arg1, const void *arg2 )  
{  
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );  
}  
```  
  
```Output  
wordlist before _lsearch: hello thanks bye  
wordlist after _lsearch: hello thanks bye extra  
```  
  
## <a name="see-also"></a>Viz také  
 [Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch –](../../c-runtime-library/reference/bsearch.md)   
 [_lfind –](../../c-runtime-library/reference/lfind.md)   
 [_lsearch_s](../../c-runtime-library/reference/lsearch-s.md)