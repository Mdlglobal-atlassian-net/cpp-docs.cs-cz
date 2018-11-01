---
title: _lfind_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
ms.openlocfilehash: 08c04d9d1ca69998d54304c96468298013907179
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648435"
---
# <a name="lfinds"></a>_lfind_s

Provádí lineárního hledání pro zadaný klíč. Verze [_lfind –](lfind.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Objekt pro hledání.

*base*<br/>
Ukazatel na základní data vyhledávání.

*Číslo*<br/>
Počet prvků pole.

*Velikost*<br/>
Velikost prvků pole v bajtech.

*compare*<br/>
Ukazatel na rutiny porovnání. První parametr je *kontextu* ukazatele. Druhý parametr je ukazatel na klíč pro hledání. Třetí parametr je ukazatel na prvek pole, která se má porovnat s klíčem.

*Kontext*<br/>
Ukazatel na objekt, který může přistupovat ve funkci porovnání.

## <a name="return-value"></a>Návratová hodnota

Pokud je nalezen klíč, **_lfind_s –** vrací ukazatel na prvek v poli *základní* , který odpovídá *klíč*. Pokud není nalezen klíč, **_lfind_s –** vrátí **NULL**.

Pokud jsou předány neplatné parametry pro funkci, vyvolán obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, **errno** je nastavena na **EINVAL** a funkce vrátí **NULL**.

### <a name="error-conditions"></a>Chybové podmínky

|klíč|base|compare|počet|velikost|errno|
|---------|----------|-------------|---------|----------|-----------|
|**HODNOTU NULL**|Všechny|Všechny|Všechny|Všechny|**EINVAL**|
|Všechny|**HODNOTU NULL**|Všechny|!= 0|Všechny|**EINVAL**|
|Všechny|Všechny|Všechny|Všechny|nula|**EINVAL**|
|Všechny|Všechny|**HODNOTU NULL**|Aplikace|Všechny|**EINVAL**|

## <a name="remarks"></a>Poznámky

**_Lfind_s –** funkce provádí lineárního hledání pro hodnotu *klíč* v poli *číslo* prvky, každý z *šířka* bajtů. Na rozdíl od **bsearch_s –**, **_lfind_s –** nevyžaduje, aby pole, který se má seřadit. *Základní* argument je ukazatel na základní pole, které chcete prohledat. *Porovnání* argument je ukazatel na uživatelem zadané rutinou, která porovná dva prvky pole a vrátí hodnotu určující, jejich vztahu. **_lfind_s –** volání *porovnání* rutinní jednou nebo vícekrát během hledání předání *kontextu* ukazatele a odkazy na dva prvky pole při každém volání. *Porovnání* rutina musí porovnat elementy pak vrátí nenulovou hodnotu (tj., že jsou různé prvky), nebo 0 (tj. elementy jsou identické).

**_lfind_s –** je podobný **_lfind –** s výjimkou přidání *kontextu* ukazatelů do argumentů funkce porovnání a seznamu parametrů funkce. *Kontextu* ukazatele může být užitečné, pokud hledaný datová struktura je součástí objektu a *porovnání* funkce potřebuje pro přístup ke členům objektu. *Porovnání* funkce lze přetypovat ukazatele do příslušného objektu typu a přístup členů tohoto objektu. Přidání *kontextu* parametr díky **_lfind_s –** bezpečnější, protože další kontext je možné, aby se zabránilo vícenásobnému přístupu chyb spojených s použitím statické proměnné pro zpřístupnění dat pro *porovnání* funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_lfind_s**|\<Search.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Vyhledávání a třídění](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort_s](qsort-s.md)<br/>
[_lfind](lfind.md)<br/>
