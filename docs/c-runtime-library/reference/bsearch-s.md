---
title: "bsearch_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: bsearch_s
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
f1_keywords: bsearch_s
dev_langs: C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19d60e16ee896049318d8722b59ba124aad67a50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bsearchs"></a>bsearch_s
Provede binární vyhledávání seřazené pole. Toto je verze [bsearch –](../../c-runtime-library/reference/bsearch.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *bsearch_s(   
   const void *key,  
   const void *base,  
   size_t num,  
   size_t width,  
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),  
   void * context  
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
 Funkce zpětného volání, který porovnává dva elementy. První argument je `context` ukazatel. Druhý argument je ukazatel `key` pro hledání. Třetí argument je ukazatel na element pole, který se má porovnat s `key`.  
  
 `context`  
 Ukazatel na objekt, který je přístupná ve funkci porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 `bsearch_s`vrací ukazatel na výskyt `key` v poli, na kterou odkazuje `base`. Pokud `key` není nalezeno, vrátí funkce `NULL`. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, výsledkem nepředvídatelné.  
  
 Pokud jsou předány neplatné parametry pro funkce, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|||||||  
|-|-|-|-|-|-|  
|`key`|`base`|`compare`|`num`|`width`|`errno`|  
|`NULL`|všechny|všechny|všechny|všechny|`EINVAL`|  
|všechny|`NULL`|všechny|!= 0|všechny|`EINVAL`|  
|všechny|všechny|všechny|všechny|= 0|`EINVAL`|  
|všechny|všechny|`NULL`|k|všechny|`EINVAL`|  
  
## <a name="remarks"></a>Poznámky  
 `bsearch_s` Funkce provádí binární hledání seřazené pole `num` elementy, každý z `width` velikost bajtů. `base` Hodnota je ukazatel na základní pole má proběhnout, a `key` je hodnota vyhledané. `compare` Parametr je ukazatel na uživatelem zadané rutiny, který porovnává požadovaný klíč k elementu pole a vrátí jednu z následujících hodnot zadání jejich relace:  
  
|Hodnoty vrácené `compare` rutiny|Popis|  
|-----------------------------------------|-----------------|  
|\< 0|Klíč je menší než pole elementu.|  
|0|Klíč se rovná pole elementu.|  
|> 0|Klíč je větší než pole elementu.|  
  
 `context` Ukazatel můžou být užitečné, pokud vyhledávaná datovou strukturu je součástí objektu a funkci porovnání potřebuje pro přístup ke členům v objektu. `compare` Funkce může void ukazatele přetypování do příslušného objektu typu a přístupu členů tohoto objektu. Přidání `context` parametr díky `bsearch_s` bezpečnější, protože další kontext může sloužit k vyhnout opětovné zadání chyby související s použitím statické proměnné pro zpřístupnění dat pro `compare` funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`bsearch_s`|\<stdlib.h > a \<search.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Tento program seřadí řetězců se [qsort_s –](../../c-runtime-library/reference/qsort-s.md)a potom bsearch_s – používá k nalezení slovo "kočka".  
  
```  
// crt_bsearch_s.cpp  
// This program uses bsearch_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
#define ENGLISH_LOCALE "English_US.850"  
#endif  
  
#ifdef CODEPAGE_1252  
#define ENGLISH_LOCALE "English_US.1252"  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, char **str1, char **str2)  
{  
    char *s1 = *str1;  
    char *s2 = *str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
int main( void )  
{  
   char *arr[] = {"dog", "pig", "horse", "cat", "human", "rat", "cow", "goat"};  
  
   char *key = "cat";  
   char **result;  
   int i;  
  
   /* Sort using Quicksort algorithm: */  
   qsort_s( arr,  
            sizeof(arr)/sizeof(arr[0]),  
            sizeof( char * ),  
            (int (*)(void*, const void*, const void*))compare,  
            &locale(ENGLISH_LOCALE) );  
  
   for( i = 0; i < sizeof(arr)/sizeof(arr[0]); ++i )    /* Output sorted list */  
      printf( "%s ", arr[i] );  
  
   /* Find the word "cat" using a binary search algorithm: */  
   result = (char **)bsearch_s( &key,  
                                arr,  
                                sizeof(arr)/sizeof(arr[0]),  
                                sizeof( char * ),  
                                (int (*)(void*, const void*, const void*))compare,  
                                &locale(ENGLISH_LOCALE) );  
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
 [qsort](../../c-runtime-library/reference/qsort.md)