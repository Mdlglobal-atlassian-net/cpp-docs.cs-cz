---
title: "bsearch – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: bsearch
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
f1_keywords: bsearch
dev_langs: C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch function
ms.assetid: e0ad2f47-e7dd-49ed-8288-870457a14a2c
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a7166570785d2d73db06fcdf7e42492317621a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bsearch"></a>bsearch
Provede binární vyhledávání seřazené pole. Bezpečnější verze této funkce je k dispozici. v tématu [bsearch_s –](../../c-runtime-library/reference/bsearch-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *bsearch(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) (const void *key, const void *datum)   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Objekt, který chcete vyhledat.  
  
 `base`  
 Ukazatel na základní dat hledání.  
  
 `num`  
 Počet elementů.  
  
 `width`  
 Šířka elementů.  
  
 `compare`  
 Funkce zpětného volání, který porovnává dva elementy. První je ukazatel na klíč pro hledání a druhý je ukazatel na element pole, který se má porovnat s klíčem.  
  
## <a name="return-value"></a>Návratová hodnota  
 `bsearch`vrací ukazatel na výskyt `key` v poli, na kterou odkazuje `base`. Pokud `key` není nalezeno, vrátí funkce `NULL`. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, výsledkem nepředvídatelné.  
  
## <a name="remarks"></a>Poznámky  
 `bsearch` Funkce provádí binární hledání seřazené pole `num` elementy, každý z `width` velikost bajtů. `base` Hodnota je ukazatel na základní pole má proběhnout, a `key` je hodnota vyhledané. `compare` Parametr je ukazatel na uživatelem zadané rutiny, který porovnává požadovaný klíč k elementu pole a vrátí jednu z následujících hodnot zadání jejich relace:  
  
|Hodnoty vrácené `compare` rutiny|Popis|  
|-----------------------------------------|-----------------|  
|\< 0|Klíč je menší než pole elementu.|  
|0|Klíč se rovná pole elementu.|  
|> 0|Klíč je větší než pole elementu.|  
  
 Tato funkce ověří jeho parametry. Pokud `compare`, `key` nebo `num` je `NULL`, nebo pokud `base` je `NULL` a *`num` je nenulové hodnoty, nebo pokud `width` rovná nule, je volána obslužná rutina neplatný parametr, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`bsearch`|\<stdlib.h > a \<search.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento program seřadí pole řetězců qsort – a poté bsearch – používá k nalezení slovo "kočka".  
  
```  
// crt_bsearch.c  
#include <search.h>  
#include <string.h>  
#include <stdio.h>  
  
int compare( char **arg1, char **arg2 )  
{  
   /* Compare all of both strings: */  
   return _strcmpi( *arg1, *arg2 );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
   char **result;  
   char *key = "cat";  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort( (void *)arr, sizeof(arr)/sizeof(arr[0]), sizeof( char * ), (int (*)(const   
   void*, const void*))compare );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch( (char *) &key, (char *)arr, sizeof(arr)/sizeof(arr[0]),  
                              sizeof( char * ), (int (*)(const void*, const void*))compare );  
   if( result )  
      printf( "\n%s found at %Fp\n", *result, result );  
   else  
      printf( "\nCat not found!\n" );  
}  
```  
  
```Output  
cat cow dog goat horse human pig rat  
cat found at 002F0F04  
```  
  
## <a name="see-also"></a>Viz také  
 [Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)   
 [_lfind –](../../c-runtime-library/reference/lfind.md)   
 [_lsearch –](../../c-runtime-library/reference/lsearch.md)   
 [qsort –](../../c-runtime-library/reference/qsort.md)