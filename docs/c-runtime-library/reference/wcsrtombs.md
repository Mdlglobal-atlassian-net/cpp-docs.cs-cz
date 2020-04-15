---
title: wcsrtombs
ms.date: 4/2/2020
api_name:
- wcsrtombs
- _o_wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: af22a7d55c5f4958db6962e98f212fb5bb89e61e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328062"
---
# <a name="wcsrtombs"></a>wcsrtombs

Převeďte široký řetězec znaků na reprezentaci vícebajtového znakového řetězce. K dispozici je bezpečnější verze této funkce. viz [wcsrtombs_s](wcsrtombs-s.md).

## <a name="syntax"></a>Syntaxe

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Výsledné umístění adresy řetězce vícebajtových znaků.

*wcstr*<br/>
Nepřímo odkazuje na umístění řetězce široký znak, který má být převeden.

*Počet*<br/>
Počet znaků, které mají být převedeny.

*mbstate*<br/>
Ukazatel na **objekt stavu mbstate_t** převodu.

## <a name="return-value"></a>Návratová hodnota

Vrátí počet úspěšně převedených bajtů, bez hodnoty null ukončujícího nulového bajtu (pokud existuje), jinak -1, pokud došlo k chybě.

## <a name="remarks"></a>Poznámky

Funkce **wcsrtombs** převede řetězec širokých znaků počínaje zadaným stavem převodu obsaženým v *mbstate*z nepřímých hodnot v *wcstr*na adresu *mbstr*. Převod bude pokračovat pro každý znak, dokud: po null ukončující široký znak je zjištěn, když je zjištěn neodpovídající znak nebo když další znak by překročit limit obsažený v *count*. Pokud **wcsrtombs** narazí na znak null široký znak (L'\0') před nebo při *počítání* dojde, převede jej na 8bitový 0 a zastaví.

Vícebajtový znakový řetězec na *mbstr* je tedy ukončen a nula pouze v případě, **že wcsrtombs** narazí na široký znak null znak u převodu. Pokud se sekvence, na které se překrývají *wcstr* a *mbstr,* chování **wcsrtombs** není definováno. **wcsrtombs** je ovlivněna LC_TYPE kategorie aktuální národní prostředí.

Funkce **wcsrtombs** se liší od [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) svou restartovatelností. Stav převodu je uložen v *mbstate* pro následná volání stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí.  Například aplikace by použít **wcsrlen** spíše než **wcsnlen**, pokud následné volání **wcsrtombs** byly použity namísto **wcstombs**.

Pokud je argument *mbstr* **null**, **vrátí wcsrtombs** požadovanou velikost v bajtech cílového řetězce. Pokud *mbstate* je null, je použit vnitřní **mbstate_t** stavu převodu. Pokud sekvence znaků *wchar* nemá odpovídající vícebajtovou reprezentaci znaků, je vrácena -1 a **errno** je nastaveno na **EILSEQ**.

V jazyce C++ má tato funkce přetížení šablony, která vyvolá novější, bezpečný protějšek této funkce. Další informace naleznete [v tématu Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="exceptions"></a>Výjimky

Funkce **wcsrtombs** je bezpečná pro více vláken, pokud žádná funkce v aktuálním vlákně volá **setlocale,** zatímco tato funkce je spuštěna a *mbstate* není null.

## <a name="example"></a>Příklad

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wcsrtombs**|\<wchar.h>|

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
