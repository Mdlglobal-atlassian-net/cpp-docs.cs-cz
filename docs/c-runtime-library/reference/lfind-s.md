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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 589a413c9f1fb49fbfe8cd1b5eacb9d452716523
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916504"
---
# <a name="_lfind_s"></a>_lfind_s

Provede lineární hledání zadaného klíče. Verze [_lfind](lfind.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*zkrat*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základ dat hledání.

*Automatické*<br/>
Počet prvků pole.

*hodnota*<br/>
Velikost prvků pole v bajtech

*porovnán*<br/>
Ukazatel na srovnávací rutinu. První parametr je *kontextový* ukazatel. Druhým parametrem je ukazatel na klíč pro hledání. Třetí parametr je ukazatel na prvek pole, který má být porovnán s klíčem.

*souvislost*<br/>
Ukazatel na objekt, který je pravděpodobně k dispozici ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud je klíč nalezen, **_lfind_s** vrátí ukazatel na prvek pole na *bázi Base* , který odpovídá *klíči*. Pokud klíč nebyl nalezen, **_lfind_s** vrátí **hodnotu null**.

Pokud jsou funkci předány neplatné parametry, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, **errno** je nastaven na **EINVAL** a funkce vrátí **hodnotu null**.

### <a name="error-conditions"></a>Chybové stavy

|key|base|compare|num|velikost|errno|
|---------|----------|-------------|---------|----------|-----------|
|**PLATNOST**|jakýmikoli|jakýmikoli|jakýmikoli|jakýmikoli|**EINVAL**|
|jakýmikoli|**PLATNOST**|jakýmikoli|! = 0|jakýmikoli|**EINVAL**|
|jakýmikoli|jakýmikoli|jakýmikoli|jakýmikoli|nula|**EINVAL**|
|jakýmikoli|jakýmikoli|**PLATNOST**|an|jakýmikoli|**EINVAL**|

## <a name="remarks"></a>Poznámky

Funkce **_lfind_s** provede lineární hledání *klíč* hodnoty v poli *číselných* prvků, přičemž každý z nich má *šířku* . Na rozdíl **bsearch_s**od bsearch_s **_lfind_s** nevyžaduje řazení pole. *Základní* argument je ukazatel na základ pole, které má být prohledáno. Argument *Compare* je ukazatel na uživatelsky zadanou rutinu, která porovnává dva prvky pole a vrátí hodnotu určující jejich relaci. **_lfind_s** volá rutinu *porovnání* jednou nebo vícekrát během hledání, předá ukazatel na *kontext* a ukazatele na dva prvky pole při každém volání. Rutina *porovnání* musí porovnat prvky a pak vracet nenulové (to znamená, že prvky jsou rozdílné) nebo 0 (což znamená, že prvky jsou identické).

**_lfind_s** je podobná **_lfind** s výjimkou přidání *kontextového* ukazatele na argumenty funkce porovnání a seznamu parametrů funkce. *Kontextový* ukazatel může být užitečný, pokud je struktura prohledávaných dat součástí objektu a funkce *Compare* potřebuje přístup k členům objektu. Funkce *Compare* může přetypovat ukazatel void na příslušný typ objektu a přistupovat ke členům tohoto objektu. Přidání *kontextového* parametru vede **_lfind_sější** zabezpečením, protože další kontext lze použít k tomu, aby se předešlo Vícenásobný přístup chybám přidruženým k použití statických proměnných, aby byla k dispozici data pro funkci *Compare* .

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind_s**|\<Hledat. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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

[Hledání a řazení](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
