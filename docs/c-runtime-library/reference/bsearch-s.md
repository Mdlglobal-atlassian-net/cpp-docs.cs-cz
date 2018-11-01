---
title: bsearch_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- arrays [CRT], binary search
- bsearch_s function
ms.assetid: d5690d5e-6be3-4f1d-aa0b-5ca6dbded276
ms.openlocfilehash: cd621c1dae2cae847bbbf032dec7e6972c526203
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430833"
---
# <a name="bsearchs"></a>bsearch_s

Provádí binární vyhledávání seřazené pole. Toto je verze [bsearch –](bsearch.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Objekt pro hledání.

*base*<br/>
Ukazatele na základní dat hledání.

*Číslo*<br/>
Počet prvků.

*Šířka*<br/>
Šířka prvků.

*compare*<br/>
Funkce zpětného volání, která porovná dva elementy. První argument je *kontextu* ukazatele. Druhý argument je ukazatel *klíč* pro hledání. Třetí argument je ukazatel na prvek pole, která se má porovnat s *klíč*.

*Kontext*<br/>
Ukazatel na objekt, který je přístupný ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

**bsearch_s –** vrací ukazatel na výskyt *klíč* pole, na které odkazuje *základní*. Pokud *klíč* nenajde, vrátí funkce hodnotu **NULL**. Pokud pole není ve vzestupném pořadí řazení nebo obsahuje duplicitní záznamy s identickými klíči, je výsledkem nepředvídatelné.

Pokud neplatné parametry jsou předány funkci, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**. Další informace najdete v tématu [errno _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Chybové podmínky

|||||||
|-|-|-|-|-|-|
|*Klíč*|*base*|*compare*|*Číslo*|*Šířka*|**errno**|
|**HODNOTU NULL**|Všechny|Všechny|Všechny|Všechny|**EINVAL**|
|Všechny|**HODNOTU NULL**|Všechny|!= 0|Všechny|**EINVAL**|
|Všechny|Všechny|Všechny|Všechny|= 0|**EINVAL**|
|Všechny|Všechny|**HODNOTU NULL**|Aplikace|Všechny|**EINVAL**|

## <a name="remarks"></a>Poznámky

**Bsearch_s –** funkce provádí binárního vyhledávání seřazené pole *číslo* prvky, každý z *šířka* bajty. *Základní* hodnota je ukazatel na základní pole pro hledání, a *klíč* je hodnota vyhledané. *Porovnání* parametrem je ukazatel do uživatelem zadané rutinu, která porovnává požadovaný klíč k elementu pole a vrátí jednu z následujících hodnot zadáním jejich vztahu:

|Hodnota vrácená *porovnání* rutina|Popis|
|-----------------------------------------|-----------------|
|\< 0|Klíč je menší než prvek pole.|
|0|Klíč je rovna prvek pole.|
|> 0|Klíč je větší než prvek pole.|

*Kontextu* ukazatele může být užitečné, pokud hledaný datová struktura je součástí objektu a funkce porovnání potřebuje pro přístup ke členům objektu. *Porovnání* funkce může přetypovat ukazatel void do příslušného objektu typu a přístup členů tohoto objektu. Přidání *kontextu* parametr díky **bsearch_s –** bezpečnější, protože další kontext lze zabránit vícenásobnému přístupu chyb spojených s použitím statické proměnné pro zpřístupnění dat pro *porovnání* funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**bsearch_s**|\<stdlib.h > a \<search.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program řadí pole řetězců s [qsort_s –](qsort-s.md)a potom pomocí bsearch_s – vyhledejte slovo "cat".

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

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
