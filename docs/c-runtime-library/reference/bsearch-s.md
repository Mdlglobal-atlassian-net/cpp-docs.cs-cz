---
title: bsearch_s
ms.date: 4/2/2020
api_name:
- bsearch_s
- _o_bsearch_s
api_location:
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- bsearch_s
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: ef8a68f0db45e718af6b17fe0d08c33a6fd61d6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333837"
---
# <a name="bsearch_s"></a>bsearch_s

Provede binární hledání seřazené pole. Tato funkce je verze [bsearch](bsearch.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Klíč*\
Ukazatel na klíč, který chcete vyhledat.

*Základní*\
Ukazatel na základnu vyhledávacích dat.

*Číslo*\
Počet prvků.

*Šířka*\
Šířka prvků.

*Porovnat*\
Funkce zpětného volání, která porovnává dva prvky. První argument je ukazatel *kontextu.* Druhý argument je ukazatel na *klíč* pro hledání. Třetí argument je ukazatel na prvek pole, který má být porovnán s *klíčem*.

*Kontextu*\
Ukazatel na objekt, který lze přistupovat ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

**bsearch_s** vrátí ukazatel na výskyt *klíče* v poli, na které odkazuje *základna*. Pokud *klíč* nebyl nalezen, funkce vrátí **hodnotu NULL**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, výsledek je nepředvídatelný.

Pokud jsou funkci předány neplatné parametry, vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**. Další informace naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|||||||
|-|-|-|-|-|-|
|*key*|*base*|*Porovnat*|*Číslo*|*Šířka*|**errno**|
|**Null**|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|
|jakékoli|**Null**|jakékoli|!= 0|jakékoli|**EINVAL**|
|jakékoli|jakékoli|jakékoli|jakékoli|= 0|**EINVAL**|
|jakékoli|jakékoli|**Null**|an|jakékoli|**EINVAL**|

## <a name="remarks"></a>Poznámky

Funkce **bsearch_s** provádí binární vyhledávání seřazené pole *číselných* prvků, každý *šířka* bajtů ve velikosti. *Základní* hodnota je ukazatel na základnu pole, které má být prohledáno, a *klíč* je požadovaná hodnota. Parametr *porovnání* je ukazatel na rutinu dodanou uživatelem, která porovnává požadovaný klíč s elementem pole a vrací jednu z následujících hodnot určujících jejich vztah:

|Hodnota vrácená *pomocí rutiny porovnání*|Popis|
|-----------------------------------------|-----------------|
|\<0|Klíč je menší než prvek pole.|
|0|Klíč se rovná prvku pole.|
|> 0|Klíč je větší než prvek pole.|

Ukazatel *kontextu* může být užitečné, pokud je struktura prohledávaná data součástí objektu a funkce porovnání potřebuje přístup k členům objektu. Funkce *porovnání* může přetypování ukazatele void do příslušného typu objektu a přístup členů tohoto objektu. Přidání *parametru context* umožňuje **bsearch_s** bezpečnější, protože další kontext lze použít, aby se zabránilo reentrancy chyby spojené s použitím statických proměnných zpřístupnit data pro *funkci porovnání.*

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h> \<a search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program seřadí pole řetězců s [qsort_s](qsort-s.md)a potom použije bsearch_s k nalezení slova "kočka".

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

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
