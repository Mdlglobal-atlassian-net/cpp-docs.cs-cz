---
title: wcrtomb_s
ms.date: 4/2/2020
api_name:
- wcrtomb_s
- _o_wcrtomb_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: ee25b18bfbb86b34e46c8c6776e8ab83157613e8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328173"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Převeďte široký znak na reprezentaci vícebajtových znaků. Verze [wcrtomb](wcrtomb.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Vrátí počet zapsaných bajtů nebo -1, pokud došlo k chybě.

*mbchar*<br/>
Výsledný vícebajtový převedený znak.

*sizeOfmbchar*<br/>
Velikost proměnné *mbchar* v bajtech.

*Wchar*<br/>
Široký znak převést.

*mbstate*<br/>
Ukazatel na **mbstate_t** objekt.

## <a name="return-value"></a>Návratová hodnota

Vrátí **nulovou** nebo chybnou hodnotu, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **wcrtomb_s** převede široký znak začínající v zadaném stavu převodu obsaženém v *mbstate*z hodnoty obsažené v *wchar*na adresu reprezentovanou *nástrojem mbchar*. Hodnota *pReturnValue* bude počet převedených bajtů, ale ne více než **MB_CUR_MAX** bajtů nebo -1, pokud došlo k chybě.

Pokud *mbstate* je null, je použit vnitřní **mbstate_t** stavu převodu. Pokud znak obsažený v *wchar* nemá odpovídající vícebajtový znak, hodnota *pReturnValue* bude -1 a funkce vrátí hodnotu **errno** **EILSEQ**.

Funkce **wcrtomb_s** se liší od [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) jeho restartability. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí. Například aplikace by použít **wcsrlen** spíše než **wcslen**, pokud následné volání **wcsrtombs_s** byly použity namísto **wcstombs_s**.

V jazyce C++ je použití této funkce zjednodušeno přetížením šablony; přetížení lze odvodit délku vyrovnávací paměti automaticky (eliminuje potřebu zadat argument velikosti) a mohou automaticky nahradit starší, nezabezpečené funkce s jejich novější, bezpečné protějšky. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Funkce **wcrtomb_s** je bezpečné pro více vláken, pokud žádná funkce v aktuálním podprocesu volá **setlocale,** zatímco tato funkce je spuštěna a *mbstate* je null.

## <a name="example"></a>Příklad

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
