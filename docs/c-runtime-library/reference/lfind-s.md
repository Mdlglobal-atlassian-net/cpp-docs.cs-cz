---
title: _lfind_s
ms.date: 4/2/2020
api_name:
- _lfind_s
- _o__lfind_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lfind_s
- _lfind_s
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 8f2983bee93c623eb936ed12422134281418076b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342189"
---
# <a name="_lfind_s"></a>_lfind_s

Provede lineární hledání zadaného klíče. Verze [_lfind](lfind.md) s vylepšeními zabezpečení, jak je popsáno v [části Funkce zabezpečení v crt](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
void *_lfind_s(
   const void *key,
   const void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základnu vyhledávacích dat.

*Číslo*<br/>
Počet prvků pole.

*Velikost*<br/>
Velikost prvků pole v bajtů.

*Porovnat*<br/>
Ukazatel na srovnávací rutinu. První parametr je ukazatel *kontextu.* Druhý parametr je ukazatel na klíč pro vyhledávání. Třetí parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

*Kontextu*<br/>
Ukazatel na objekt, který může být přístupný ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, **_lfind_s** vrátí ukazatel na prvek pole na *základně,* který odpovídá *klíči*. Pokud klíč nebyl nalezen, **vrátí _lfind_s** **hodnotu NULL**.

Pokud jsou funkci předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [části Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, **je chybné číslo** nastaveno na **hodnotu EINVAL** a funkce vrátí **hodnotu NULL**.

### <a name="error-conditions"></a>Chybové stavy

|key|base|compare|num|velikost|errno|
|---------|----------|-------------|---------|----------|-----------|
|**Null**|jakékoli|jakékoli|jakékoli|jakékoli|**EINVAL**|
|jakékoli|**Null**|jakékoli|!= 0|jakékoli|**EINVAL**|
|jakékoli|jakékoli|jakékoli|jakékoli|nula|**EINVAL**|
|jakékoli|jakékoli|**Null**|an|jakékoli|**EINVAL**|

## <a name="remarks"></a>Poznámky

Funkce **_lfind_s** provádí lineární hledání *klíče* hodnoty v poli *číselných* prvků, každý z *šířky* bajtů. Na rozdíl od **bsearch_s** **_lfind_s** nevyžaduje řazení pole. *Základní* argument je ukazatel na základnu pole, které má být prohledáno. Argument *porovnání* je ukazatel na rutinu dodanou uživatelem, která porovnává dva prvky pole a pak vrátí hodnotu určující jejich vztah. **_lfind_s** volání *porovnání* rutiny jednou nebo vícekrát během hledání, předávání *ukazatele kontextu* a ukazatele na dva prvky pole na každé volání. Porovnání *compare* rutina musí porovnat prvky pak vrátit nenulovou (což znamená, že prvky jsou různé) nebo 0 (což znamená, že prvky jsou identické).

**_lfind_s** je podobná **_lfind** s výjimkou přidání ukazatele *kontextu* k argumentům funkce porovnání a seznamu parametrů funkce. Ukazatel *kontextu* může být užitečné, pokud je struktura prohledávaná data součástí objektu a funkce *porovnání* potřebuje přístup k členům objektu. Funkce *porovnání* může přetypovat ukazatel void do příslušného typu objektu a přistupovat k členům tohoto objektu. Přidání *parametru context* umožňuje **_lfind_s** bezpečnější, protože další kontext lze použít, aby se zabránilo reentrancy chyby spojené s použitím statických proměnných zpřístupnit data pro *funkci porovnání.*

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind_s**|\<search.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```cpp
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

[Vyhledávání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
