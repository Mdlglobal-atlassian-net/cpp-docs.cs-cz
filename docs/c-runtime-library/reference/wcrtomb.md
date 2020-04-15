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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: eda857b80404aebe46b090741e0b56d4fe692f34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328099"
---
# <a name="wcrtomb"></a>wcrtomb

Převeďte široký znak na reprezentaci vícebajtových znaků. K dispozici je bezpečnější verze této funkce. viz [wcrtomb_s](wcrtomb-s.md).

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

*Wchar*<br/>
Široký znak převést.

*mbstate*<br/>
Ukazatel na **mbstate_t** objekt.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet bajtů potřebných k reprezentaci převedeného vícebajtového znaku, jinak -1, pokud dojde k chybě.

## <a name="remarks"></a>Poznámky

Funkce **wcrtomb** převede široký znak začínající v zadaném stavu převodu obsaženém v *mbstate*z hodnoty obsažené v *wchar*na adresu reprezentovanou *nástrojem mbchar*. Vrácená hodnota je počet bajtů požadovaných k reprezentaci odpovídajícího vícebajtového znaku, ale nevrátí více než **MB_CUR_MAX** bajtů.

Pokud *mbstate* je null, vnitřní **mbstate_t** objekt obsahující stav převodu *mbchar* se používá. Pokud sekvence znaků *wchar* nemá odpovídající vícebajtovou reprezentaci znaků, je vrácena -1 a **errno** je nastaveno na **EILSEQ**.

Funkce **wcrtomb** se liší od [wctomb, _wctomb_l](wctomb-wctomb-l.md) svou restartovatelností. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí. Například aplikace by použít **wcsrlen** spíše než **wcsnlen**, pokud následné volání **wcsrtombs** byly použity namísto **wcstombs**.

V jazyce C++ má tato funkce přetížení šablony, která vyvolá novější, zabezpečené protějšky této funkce. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

**Wcrtomb** Funkce je multithread bezpečné tak dlouho, dokud žádná funkce v aktuální vlákno volání **setlocale** při provádění této funkce a *zatímco mbstate* je null.

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
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
