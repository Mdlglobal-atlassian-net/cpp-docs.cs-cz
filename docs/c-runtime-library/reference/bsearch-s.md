---
title: bsearch_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- bsearch_s
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
- bsearch_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2600b77031967bec5d5dd549a7dd8f34fc5c5e3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="bsearchs"></a>bsearch_s

Provede binární vyhledávání seřazené pole. Toto je verze [bsearch –](bsearch.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *bsearch_s(
   const void *key,
   const void *base,
   size_t number,
   size_t width,
   int ( __cdecl *compare ) ( void *, const void *key, const void *datum),
   void * context
);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základní dat hledání.

*Číslo*<br/>
Počet elementů.

*Šířka*<br/>
Šířka elementů.

*compare*<br/>
Funkce zpětného volání, který porovnává dva elementy. První argument je *kontextu* ukazatel. Druhý argument je ukazatel *klíč* pro hledání. Třetí argument je ukazatel na element pole, který se má porovnat s *klíč*.

*Kontext*<br/>
Ukazatel na objekt, který je přístupná ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

**bsearch_s –** vrací ukazatel na výskyt *klíč* v poli, na kterou odkazuje *základní*. Pokud *klíč* není nalezeno, vrátí funkce **NULL**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, výsledkem nepředvídatelné.

Pokud jsou předány neplatné parametry pro funkce, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **NULL**. Další informace najdete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|||||||
|-|-|-|-|-|-|
|*Klíč*|*base*|*compare*|*Číslo*|*Šířka*|**Kód chyby**|
|**HODNOTU NULL**|všechny|všechny|všechny|všechny|**EINVAL –**|
|všechny|**HODNOTU NULL**|všechny|!= 0|všechny|**EINVAL –**|
|všechny|všechny|všechny|všechny|= 0|**EINVAL –**|
|všechny|všechny|**HODNOTU NULL**|k|všechny|**EINVAL –**|

## <a name="remarks"></a>Poznámky

**Bsearch_s –** funkce provádí binární hledání seřazené pole *číslo* elementy, každý z *šířka* velikost bajtů. *Základní* hodnota je ukazatel na základní pole má proběhnout, a *klíč* je hodnota vyhledané. *Porovnat* parametr je ukazatel na uživatelem zadané rutiny, který porovnává požadovaný klíč k elementu pole a vrátí jednu z následujících hodnot zadání jejich relace:

|Hodnoty vrácené *porovnat* rutiny|Popis|
|-----------------------------------------|-----------------|
|\< 0|Klíč je menší než pole elementu.|
|0|Klíč se rovná pole elementu.|
|> 0|Klíč je větší než pole elementu.|

*Kontextu* ukazatel můžou být užitečné, pokud vyhledávaná datovou strukturu je součástí objektu a funkci porovnání potřebuje pro přístup ke členům v objektu. *Porovnat* funkce může void ukazatele přetypování do příslušného objektu typu a přístupu členů tohoto objektu. Přidání *kontextu* parametr díky **bsearch_s –** bezpečnější, protože další kontext může sloužit k vyhnout opětovné zadání chyby související s zpřístupnit data pomocí statické proměnné *porovnat* funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h > a \<search.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program seřadí řetězců se [qsort_s –](qsort-s.md)a potom bsearch_s – používá k nalezení slovo "kočka".

```cpp
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

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
