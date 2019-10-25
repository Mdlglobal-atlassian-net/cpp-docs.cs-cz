---
title: bsearch_s
ms.date: 10/22/2019
api_name:
- bsearch_s
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
ms.openlocfilehash: fc86576dbbe73f63da6bf0e28e7166ef7c552e55
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811142"
---
# <a name="bsearch_s"></a>bsearch_s

Provede binární hledání seřazeného pole. Tato funkce je verze [bSearch](bsearch.md) s vylepšením zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

\ *klíčů*
Ukazatel na klíč, který chcete vyhledat.

*základní*\
Ukazatel na základ dat hledání.

\ *číslo*
Počet elementů.

\ *šířky*
Šířka prvků

*porovnat*\
Funkce zpětného volání, která porovnává dva elementy. První argument je *kontextový* ukazatel. Druhý argument je ukazatel na *klíč* pro hledání. Třetí argument je ukazatel na prvek pole, který má být porovnán s *klíčem*.

\ *kontextu*
Ukazatel na objekt, který je možné použít ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

**bsearch_s** vrací ukazatel na výskyt *klíče* v poli, na které ukazuje *základ*. Pokud *klíč* není nalezen, funkce vrátí **hodnotu null**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy se stejnými klíči, výsledek je nepředvídatelné.

Pokud jsou do funkce předány neplatné parametry, vyvolá neplatnou obslužnou rutinu parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**. Další informace najdete v tématech [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové stavy

|||||||
|-|-|-|-|-|-|
|*zkrat*|*base*|*porovnán*|*Automatické*|*Délk*|**errno**|
|**PLATNOST**|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|**EINVAL**|
|Jakýmikoli|**PLATNOST**|Jakýmikoli|! = 0|Jakýmikoli|**EINVAL**|
|Jakýmikoli|Jakýmikoli|Jakýmikoli|Jakýmikoli|= 0|**EINVAL**|
|Jakýmikoli|Jakýmikoli|**PLATNOST**|k|Jakýmikoli|**EINVAL**|

## <a name="remarks"></a>Poznámky

Funkce **bsearch_s** provádí binární hledání seřazeného pole *číselného* prvku, přičemž každý z nich má velikost *v bajtech* . *Základní* hodnota je ukazatel na základ pole, které má být prohledáno, a *klíč* je hledaná hodnota. Parametr *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovnává požadovaný klíč s prvkem pole a vrací jednu z následujících hodnot, které určují jejich vztah:

|Hodnota vrácená rutinou *Compare*|Popis|
|-----------------------------------------|-----------------|
|\< 0|Klíč je menší než prvek pole.|
|0,8|Klíč je roven elementu pole.|
|> 0|Klíč je větší než prvek pole.|

*Kontextový* ukazatel může být užitečný, pokud je struktura prohledávaných dat součástí objektu a funkce Compare potřebuje přístup k členům objektu. Funkce *Compare* může přetypovat ukazatel void na příslušný typ objektu a přistupovat ke členům tohoto objektu. Přidání *kontextového* parametru vede k **bsearch_sější** zabezpečení, protože další kontext lze použít k tomu, aby se předešlo Vícenásobný přístup chybám přidruženým k použití statických proměnných, aby byla k dispozici data pro funkci *Compare* .

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch_s**|\<Stdlib. h > a \<Search. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program seřadí pole řetězců pomocí [qsort_s](qsort-s.md)a pak pomocí bsearch_s hledá slovo "Cat".

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

## <a name="see-also"></a>Viz také:

[Hledání a řazení](../../c-runtime-library/searching-and-sorting.md)\
[_lfind](lfind.md)\
[_lsearch](lsearch.md)\
[qsort](qsort.md)
