---
title: mbrlen
ms.date: 11/04/2016
api_name:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: c9559731f39db35e03f640bb30b9af3fff00cf66
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952497"
---
# <a name="mbrlen"></a>mbrlen

Určete počet bajtů, které jsou požadovány k dokončení vícebajtového znaku v aktuálním národním prostředí, s možností restartu uprostřed vícebajtového znaku.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parametry

*str*<br/>
Ukazatel na další bajt pro kontrolu v řetězci vícebajtového znaku.

*výpočtu*<br/>
Maximální počet bajtů, které mají být zkontrolovány.

*mbstate*<br/>
Ukazatel na aktuální stav posunutí počátečního bajtu *str*.

## <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

|||
|-|-|
0|Další *počet* nebo méně bajtů dokončí vícebajtovým znakem, který představuje celý znak null.
1 pro *počet*, včetně|Další *počet* nebo méně bajtů dokončí platným vícebajtovým znakem. Vrácená hodnota je počet bajtů, které dokončí vícebajtový znak.
(size_t) (-2)|Další *počet* bajtů přispívá k nekompletnímu, ale potenciálně platnému vícebajtovým znakem a byl zpracován tento *počet* bajtů.
(size_t) (-1)|Došlo k chybě kódování. Další *počet* nebo méně bajtů nepřispívají k kompletnímu a platnému vícebajtovým znakům. V tomto případě je **errno** nastaveno na EILSEQ a stav konverze v *mbstate* není specifikováno.

## <a name="remarks"></a>Poznámky

Funkce **mbrlen** kontroluje *maximálně bajtů, počínaje bajtem* , který ukazuje na *str* , aby určil počet bajtů, které jsou nutné k dokončení dalšího vícebajtového znaku, včetně všech sekvencí posunutí. Je ekvivalentní volání `mbrtowc(NULL, str, count, &mbstate)` , kde *mbstate* je buď uživatelem poskytnutý objekt **mbstate_t** , nebo statický interní objekt poskytnutý knihovnou.

Funkce **mbrlen** ukládá a používá stav posunu neúplného vícebajtového znaku v parametru *mbstate* . To dává **mbrlen** schopnost restartovat za běhu vícebajtového znaku, pokud je to potřeba, zkoumání na nejvyšší *počet* bajtů. Pokud je *mbstate* ukazatel s hodnotou null, používá **mbrlen** vnitřní, statický objekt **mbstate_t** k uložení stavu posunu. Vzhledem k tomu, že interní objekt **mbstate_t** není bezpečný pro přístup z více vláken, doporučujeme vždy přidělit a předat vlastní parametr *mbstate* .

Funkce **mbrlen** se liší od [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) podle jejich restartu. Stav posunu je uložený v *mbstate* pro následná volání do stejných nebo jiných restartných funkcí. Výsledky nejsou definovány při kombinování použití opakovaných a nerestartů funkcí.  Například aplikace by měla používat **wcsrlen** namísto **wcslen** , pokud je místo **wcstombs**použito následné volání **wcsrtombs** .

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|Nelze použít|Nelze použít|**mbrlen**|Nelze použít|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak je výklad vícebajtových znaků závislý na aktuální znakové stránce, a ukazuje obnovení schopnosti **mbrlen**.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>Viz také:

[Manipulace s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
