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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 51985b008565cbe550065b85261b8beb53ed6f89
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915964"
---
# <a name="wcrtomb_s"></a>wcrtomb_s

Převést velký znak na jeho vícebajtovou reprezentaci znaků. Verze [wcrtomb](wcrtomb.md) s vylepšeními zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Vrátí počet zapsaných bajtů nebo-1, pokud došlo k chybě.

*mbchar*<br/>
Výsledný vícebajtový převedený znak.

*sizeOfmbchar*<br/>
Velikost proměnné *mbchar* v bajtech

*WCHAR*<br/>
Velký znak pro převod.

*mbstate*<br/>
Ukazatel na objekt **mbstate_t** .

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula nebo **errno** , pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **wcrtomb_s** převede velký znak počínaje zadaným stavem konverze obsaženým v *mbstate*z hodnoty v *WCHAR*na adresu reprezentovanou *mbchar*. Hodnota *pReturnValue* bude počet převedených bajtů, ale ne více než **MB_CUR_MAX** bajtů, nebo-1, pokud došlo k chybě.

Pokud má *mbstate* hodnotu null, použije se vnitřní stav konverze **mbstate_t** . Pokud znak obsažený v *WCHAR* nemá odpovídající vícebajtový znak, bude hodnota *pReturnValue* -1 a funkce vrátí hodnotu **errno** **EILSEQ**.

Funkce **wcrtomb_s** se liší od [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md) podle jejich restartu. Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí. Například aplikace bude používat **wcsrlen** namísto **wcslen**, pokud bylo použito následné volání **wcsrtombs_s** místo **wcstombs_s**.

V jazyce C++ je použití této funkce zjednodušeno pomocí přetížení šablon; přetížení můžou odvodit délku vyrovnávací paměti automaticky (eliminují nutnost zadat argument velikosti) a můžou automaticky nahradit starší nezabezpečené funkce jejich novějšími, zabezpečenými protějšky. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Funkce **wcrtomb_s** je vláknově bezpečná, dokud žádná funkce v aktuálním vlákně nevolá funkci **setlocale** při provádění této funkce a *mbstate* má hodnotu null.

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
|**wcrtomb_s**|\<WCHAR. h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
