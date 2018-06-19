---
title: _lfind_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _lfind_s
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
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 963b657a009f7376a17706b4ac1e5fb4e8b69237
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404815"
---
# <a name="lfinds"></a>_lfind_s

Provede lineárního hledání pro zadaný klíč. Verzi [_lfind –](lfind.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Klíč*<br/>
Objekt, který chcete vyhledat.

*base*<br/>
Ukazatel na základní dat hledání.

*Číslo*<br/>
Počet prvků pole.

*Velikost*<br/>
Velikost prvků pole v bajtech.

*compare*<br/>
Ukazatel na rutiny porovnání. První parametr je *kontextu* ukazatel. Druhý parametr je ukazatel na klíč pro vyhledávání. Třetí parametr není ukazatel na element pole, který se má porovnat s klíčem.

*Kontext*<br/>
Ukazatel na objekt, který může získat přístup k ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud je nalezen klíč, **_lfind_s –** vrací ukazatel na element pole v *základní* odpovídající *klíč*. Pokud není nalezen klíč, **_lfind_s –** vrátí **NULL**.

Pokud jsou předány neplatné parametry pro funkce, je obslužná rutina neplatný parametr vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **NULL**.

### <a name="error-conditions"></a>Chybové stavy

|klíč|base|compare|Poče|velikost|Kód chyby|
|---------|----------|-------------|---------|----------|-----------|
|**HODNOTU NULL**|všechny|všechny|všechny|všechny|**EINVAL –**|
|všechny|**HODNOTU NULL**|všechny|!= 0|všechny|**EINVAL –**|
|všechny|všechny|všechny|všechny|nula|**EINVAL –**|
|všechny|všechny|**HODNOTU NULL**|k|všechny|**EINVAL –**|

## <a name="remarks"></a>Poznámky

**_Lfind_s –** funkce provádí lineárního hledání pro hodnotu *klíč* v pole *číslo* elementy, každý z *šířka* bajtů. Na rozdíl od **bsearch_s –**, **_lfind_s –** nevyžaduje pole, která se má seřadit. *Základní* argument je ukazatel na základní pole má proběhnout. *Porovnat* argument je ukazatel na rutiny zadanou uživatelem, který porovná dva elementy pole a vrátí hodnotu udávající, jejich vztahu. **_lfind_s –** volání *porovnat* rutiny jeden či více krát během hledání, předávání *kontextu* ukazatele a ukazatele na dva elementy pole při každém volání. *Porovnat* rutinu musí porovnat elementy pak vrátí nenulové hodnoty (tj. že elementy se liší), nebo 0 (tj. elementy jsou identické).

**_lfind_s –** je podobná **_lfind –** s výjimkou přidání *kontextu* ukazatel na argumenty funkce porovnání a seznam parametrů funkce. *Kontextu* ukazatel může být užitečné, pokud je součástí objektu vyhledávaná datovou strukturu a *porovnat* funkce potřebujete přístup ke členům v objektu. *Porovnat* funkce může odevzdat neplatný ukazatel do příslušného objektu typu a přístupu členů tohoto objektu. Přidání *kontextu* parametr díky **_lfind_s –** bezpečnější, protože další kontext umožňuje vyhnout opětovné zadání chyby související s zpřístupnit data pomocí statické proměnné *porovnat* funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind_s**|\<Search.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
