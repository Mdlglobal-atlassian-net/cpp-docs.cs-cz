---
title: strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l
ms.date: 01/22/2019
apiname:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
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
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: 5dec0c44519b78a3c4a98c51f8b8ca9bc3f54a7c
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702710"
---
# <a name="strcpys-wcscpys-mbscpys-mbscpysl"></a>strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l

Zkopíruje řetězec. Tyto verze [strcpy – wcscpy –, _mbscpy –](strcpy-wcscpy-mbscpy.md) mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscpy_s –** a **_mbscpy_s_l** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
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
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Umístění cílové vyrovnávací paměti řetězce.

*dest_size*<br/>
Velikost vyrovnávací paměti pro řetězec cílového v **char** jednotky pro funkce úzké a vícebajtové a **wchar_t** jednotky pro široké funkce. Tato hodnota musí být větší než nula, která není větší než **RSIZE_MAX**.

*src*<br/>
Vyrovnávací paměti pro řetězec zakončený hodnotou Null zdroje.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; v opačném případě chybu.

### <a name="error-conditions"></a>Chybové podmínky

|*dest*|*dest_size*|*src*|Návratová hodnota|Obsah *dest*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL**|Všechny|Všechny|**EINVAL**|Nezměněno|
|Všechny|Všechny|**NULL**|**EINVAL**|*DEST*[0] nastavit na hodnotu 0|
|Všechny|0 nebo příliš malá|Všechny|**ERANGE**|*DEST*[0] nastavit na hodnotu 0|

## <a name="remarks"></a>Poznámky

**Strcpy_s** funkce kopíruje obsah do pole adresy ve *src*, včetně ukončujícího nulového znaku do umístění, která je zadána *dest*. Cílový řetězec musí být dostatečně velký pro zdrojový řetězec a jeho ukončující znak null. Chování **strcpy_s** není definováno, pokud se zdrojový a cílový řetězec překrývají.

**wcscpy_s –** je verze širokého znaku **strcpy_s**, a **_mbscpy_s –** je vícebajtová znaková verze. Argumenty **wcscpy_s –** jsou širokoznaké řetězce **_mbscpy_s –** a **_mbscpy_s_l** jsou vícebajtové znakové řetězce. Tyto funkce chovají identicky jinak. **_mbscpy_s_l** je stejný jako **_mbscpy_s –** s tím rozdílem, že používá parametr národního prostředí namísto aktuálního národního prostředí předaného. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *dest* nebo *src* je ukazatel s hodnotou null, nebo pokud řetězec cíle velikost *dest_size* je příliš malá, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastavte **errno** k **EINVAL** při *dest* nebo  *src* je ukazatel s hodnotou null, a vrátí **ERANGE** a nastavte **errno** k **ERANGE** Pokud cílový řetězec je příliš malá.

Po úspěšném spuštění cílového řetězce je vždy zakončený hodnotou null.

V jazyce C++ je použití těchto funkcí zjednodušeno díky přetížení šablon, které dokážou odvodit velikost vyrovnávací paměti automaticky tak, že není nutné zadat argument velikosti, a dokážou automaticky nahradit starší, méně zabezpečené funkce s jejich novější, lépe zabezpečit protějšky. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).

Ladicí verze knihovny z těchto funkcí nejprve naplní vyrovnávací paměť hodnotou 0xFE. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<String.h > nebo \<wchar.h >|
|**_mbscpy_s**|\<Mbstring.h >|

Tyto funkce jsou specifické pro společnost Microsoft. Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Na rozdíl od kódu produkční kvality Tato ukázka volání funkce zabezpečený řetězec bez kontroly chyb:

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

Při sestavování kódu jazyka C++, může být jednodušší použít verze šablony.

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

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md) <br/>
[strcat, wcscat, _mbscat, _mbscat_l](strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp, _mbscmp_l](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
