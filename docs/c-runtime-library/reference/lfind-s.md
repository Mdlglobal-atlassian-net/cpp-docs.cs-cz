---
title: "_lfind_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lfind_s
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
- lfind_s
- _lfind_s
dev_langs: C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a49c732be3c1f378340d00c414acee91e6e62978
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="lfinds"></a>_lfind_s
Provede lineárního hledání pro zadaný klíč. Verzi [_lfind –](../../c-runtime-library/reference/lfind.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void *_lfind_s(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Objekt, který chcete vyhledat.  
  
 `base`  
 Ukazatel na základní dat hledání.  
  
 `num`  
 Počet prvků pole.  
  
 `size`  
 Velikost prvků pole v bajtech.  
  
 `compare`  
 Ukazatel na rutiny porovnání. První parametr je `context` ukazatel. Druhý parametr je ukazatel na klíč pro vyhledávání. Třetí parametr není ukazatel na element pole, který se má porovnat s klíčem.  
  
 `context`  
 Ukazatel na objekt, který může získat přístup k ve funkci porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je nalezen klíč, `_lfind_s` vrací ukazatel na element pole v `base` odpovídající `key`. Pokud není nalezen klíč, `_lfind_s` vrátí `NULL`.  
  
 Pokud jsou předány neplatné parametry pro funkce, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `NULL`.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|klíč|base|compare|Poče|velikost|Kód chyby|  
|---------|----------|-------------|---------|----------|-----------|  
|`NULL`|všechny|všechny|všechny|všechny|`EINVAL`|  
|všechny|`NULL`|všechny|!= 0|všechny|`EINVAL`|  
|všechny|všechny|všechny|všechny|nula|`EINVAL`|  
|všechny|všechny|`NULL`|k|všechny|`EINVAL`|  
  
## <a name="remarks"></a>Poznámky  
 `_lfind_s` Funkce provádí lineárního hledání pro hodnotu `key` v pole `num` elementy, každý z `width` bajtů. Na rozdíl od `bsearch_s`, `_lfind_s` nevyžaduje pole, která se má seřadit. `base` Argument je ukazatel na základní pole má proběhnout. `compare` Argument je ukazatel na rutiny zadanou uživatelem, který porovná dva elementy pole a vrátí hodnotu udávající, jejich vztahu. `_lfind_s`volání `compare` rutiny jeden či více krát během hledání, předávání `context` ukazatele a ukazatele na dva elementy pole při každém volání. `compare` Rutinu musí porovnat elementy pak vrátí nenulové hodnoty (tj. že elementy se liší), nebo 0 (tj. elementy jsou identické).  
  
 `_lfind_s`je podobná `_lfind` s výjimkou přidání `context` ukazatel na argumenty funkce porovnání a seznam parametrů funkce. `context` Ukazatel může být užitečné, pokud je součástí objektu vyhledávaná datovou strukturu a `compare` funkce potřebujete přístup ke členům v objektu. `compare` Funkce může odevzdat neplatný ukazatel do příslušného objektu typu a přístupu členů tohoto objektu. Přidání `context` díky parametr `_lfind_s` bezpečnější, protože další kontext umožňuje vyhnout opětovné zadání chyby spojené s použitím statické proměnné pro zpřístupnění dat `compare` funkce.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_lfind_s`|\<Search.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_lfind_s.cpp  
// This program uses _lfind_s to search a string array,  
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
// Codepage 850 is the OEM codepage used by the command line,  
// so \x00e1 is the German Sharp S  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char *s1 = *(char**)str1;  
    char *s2 = *(char**)str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
void find_it( char *key, char *array[], unsigned int num, locale &loc )  
{  
   char **result = (char **)_lfind_s( &key, array,   
                      &num, sizeof(char *), compare, &loc );  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "%s not found\n", key );  
}  
  
int main( )  
{  
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );  
}  
```  
  
```Output  
weit found  
```  
  
## <a name="see-also"></a>Viz také  
 [Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s –](../../c-runtime-library/reference/bsearch-s.md)   
 [_lsearch_s –](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort_s –](../../c-runtime-library/reference/qsort-s.md)   
 [_lfind –](../../c-runtime-library/reference/lfind.md)