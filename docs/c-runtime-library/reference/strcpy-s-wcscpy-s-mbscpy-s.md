---
title: strcpy_s – wcscpy_s –, _mbscpy_s – | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2086
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcscpy_s
- _mbscpy_s
- strcpy_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strcpy_s
- _mbscpy_s
- _tcscpy_s
- wcscpy_s
dev_langs:
- C++
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8820dbda16d95a201d666a0f25b4e06a6b79c941
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="strcpys-wcscpys-mbscpys"></a>strcpy_s, wcscpy_s, _mbscpy_s

Zkopíruje řetězec. Tyto verze nástroje [strcpy – wcscpy –, _mbscpy –](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> `_mbscpy_s` nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
```

### <a name="parameters"></a>Parametry

*Cíle*<br/>
Umístění cílové vyrovnávací paměti řetězců.

*dest_size*<br/>
Velikost cílové vyrovnávací paměti řetězců v **char** jednotky úzké a vícebajtové funkce, a **wchar_t** jednotky pro celou funkce. Tato hodnota musí být větší než 0 a menší nebo rovnou **RSIZE_MAX**.

*src*<br/>
Vyrovnávací paměť řetězce ukončené hodnotou Null zdroje.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěšného; jinak k chybě.

### <a name="error-conditions"></a>Chybové stavy

|*Cíle*|*dest_size*|*src*|Návratová hodnota|Obsah *cíle*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**HODNOTU NULL**|všechny|všechny|**EINVAL**|nedojde ke změně|
|všechny|všechny|**HODNOTU NULL**|**EINVAL**|*cíle*[0] nastaven na 0|
|všechny|0, nebo příliš malá|všechny|**ERANGE –**|*cíle*[0] nastaven na 0|

## <a name="remarks"></a>Poznámky

`strcpy_s` Funkce zkopíruje obsah v adresu *src*, včetně ukončující znak hodnoty null do umístění, která je zadána *cíle*. Cílový řetězec musí být dostatečně velký pro uložení zdrojový řetězec a jeho ukončovací znak hodnoty null. Chování `strcpy_s` není definován, pokud se překrývají zdrojové a cílové řetězce.

`wcscpy_s` je verze široká charakterová `strcpy_s`, a `_mbscpy_s` je verze vícebajtových znaků. Argumenty `wcscpy_s` jsou široká charakterová řetězce; u `_mbscpy_s` jsou řetězců vícebajtových znaků. Tyto tři funkce chovají stejně jako jinak.

Pokud *cíle* nebo *src* je ukazatel s hodnotou null, nebo pokud cíl řetězec velikost *dest_size* je příliš malá, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **einval –** a nastavte **errno** k **einval –** při *cíle* nebo  *src* je ukazatel s hodnotou null, a že budou vracet **erange –** a nastavte **errno** k **erange –** při cílový řetězec je příliš malá.

Po úspěšné provedení cílový řetězec je vždy ukončené hodnotou null.

V jazyce C++ těchto funkcí se zjednodušilo díky šabloně přetížení, které lze odvodit délka vyrovnávací paměti automaticky tak, že nemusíte určit velikost argument a starší, méně bezpečné funkce můžou automaticky nahradit s jejich novější bezpečnější svými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Verze knihovny ladění tyto funkce nejprve vyplnit vyrovnávací paměť s Bugcheck 0xFE. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcscpy_s`|`strcpy_s`|`_mbscpy_s`|`wcscpy_s`|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`strcpy_s`|\<String.h >|
|`wcscpy_s`|\<String.h > nebo \<wchar.h >|
|`_mbscpy_s`|\<Mbstring.h >|

Tyto funkce jsou specifické pro společnost Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Na rozdíl od kód produkční kvality Tato ukázka volá funkce zabezpečený řetězec bez kontroly chyb:

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char string[80];

    strcpy_s(string, _countof(string), "Hello world from ");
    strcat_s(string, _countof(string), "strcpy_s ");
    strcat_s(string, _countof(string), "and ");
    strcat_s(string, _countof(string), "strcat_s!");

    printf("String = %s\n", string);
}
```

```Output
String = Hello world from strcpy_s and strcat_s!
```

Při vytváření kódu C++, může být snazší použít šablony verze.

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t string[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(string, L"Hello world from ");
    wcscat_s(string, L"wcscpy_s ");
    wcscat_s(string, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(string, _countof(string), L"wcscat_s!");

    std::wcout << L"String = " << string << std::endl;
}
```

```Output
String = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md) <br/>
[strcat, wcscat, _mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
