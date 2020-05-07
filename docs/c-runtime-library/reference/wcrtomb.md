---
title: wcrtomb
ms.date: 4/2/2020
api_name:
- wcrtomb
- _o_wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: 4107ae6cb6366fa8ad80251ce94ee35ca59501bd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910648"
---
# <a name="wcrtomb"></a>wcrtomb

Převést velký znak na jeho vícebajtovou reprezentaci znaků. K dispozici je bezpečnější verze této funkce; viz [wcrtomb_s](wcrtomb-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Výsledný vícebajtový převedený znak.

*WCHAR*<br/>
Velký znak pro převod.

*mbstate*<br/>
Ukazatel na objekt **mbstate_t** .

## <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů, které musí představovat převedený vícebajtový znak, jinak a-1, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **wcrtomb** převede velký znak počínaje zadaným stavem konverze obsaženým v *mbstate*z hodnoty obsažené v *WCHAR*do adresy reprezentované *mbchar*. Vrácená hodnota je počet bajtů, které musí představovat odpovídající vícebajtový znak, ale nebude vracet více než **MB_CUR_MAX** bajtů.

Pokud má *mbstate* hodnotu null, použije se vnitřní objekt **mbstate_t** obsahující stav konverze *mbchar* . Pokud znak sekvence *WCHAR* neobsahuje odpovídající vícebajtovou reprezentaci znaků, je vrácena znak-1 a **errno** je nastaven na hodnotu **EILSEQ**.

Funkce **wcrtomb** se liší od [wctomb, _wctomb_l](wctomb-wctomb-l.md) podle jejich restartu. Stav konverze je uložen v *mbstate* pro následné volání stejné nebo jiné možné funkce, které lze spustit. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí. Například aplikace bude používat **wcsrlen** namísto **wcsnlen**, pokud bylo použito následné volání **wcsrtombs** namísto **wcstombs**.

V jazyce C++ Tato funkce má přetížení šablony, které vyvolává novější a zabezpečené protějšky této funkce. Další informace najdete v tématu [přetížení zabezpečení šablon](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Funkce **wcrtomb** je vláknově bezpečná, dokud žádná funkce v aktuálním vlákně nevolá funkci **setlocale** při provádění této funkce a v případě, že *mbstate* má hodnotu null.

## <a name="example"></a>Příklad

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
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
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcrtomb**|\<WCHAR. h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Jazyka](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
