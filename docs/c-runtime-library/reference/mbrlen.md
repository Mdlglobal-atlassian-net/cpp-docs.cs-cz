---
title: mbrlen
ms.date: 4/2/2020
api_name:
- mbrlen
- _o_mbrlen
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: 7503de22a8310335ddd678335916d3e74dab6e70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340993"
---
# <a name="mbrlen"></a>mbrlen

Určete počet bajtů, které jsou nutné k dokončení vícebajtového znaku v aktuálním národním prostředí, s možností restartování uprostřed vícebajtového znaku.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ukazatel na další bajt ke kontrole v řetězci vícebajtových znaků.

*Počet*<br/>
Maximální počet bajtů ke kontrole.

*mbstate*<br/>
Ukazatel na aktuální stav posunu počátečního bajtu *str*.

## <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

|||
|-|-|
0|Další *počet* nebo méně bajtů dokončit vícebajtový znak, který představuje široký znak NULL.
1 *počítat*, včetně|Další *počet* nebo méně bajtů dokončit platný vícebajtový znak. Vrácená hodnota je počet bajtů, které doplňují vícebajtový znak.
(size_t) (-2)|Další *počet* bajtů přispívají k neúplné, ale potenciálně platné vícebajtový znak a všechny *počet* bajtů byly zpracovány.
(size_t) (-1)|Došlo k chybě kódování. Další *počet* nebo méně bajtů nepřispívají k úplné a platné vícebajtový znak. V tomto případě **je chybné číslo** nastaveno na Hodnotu EILSEQ a stav převodu ve *stavu mbstate* není určen.

## <a name="remarks"></a>Poznámky

Funkce **mbrlen** kontroluje maximálně *počet* bajtů počínaje *bajtem,* na který str poukazuje, a určuje počet bajtů, které jsou nutné k dokončení dalšího vícebajtového znaku, včetně všech sekvencí posuňů. Je ekvivalentní volání, `mbrtowc(NULL, str, count, &mbstate)` kde *mbstate* je buď uživatelem poskytované **mbstate_t** objektu nebo statický vnitřní objekt poskytované knihovny.

Funkce **mbrlen** uloží a použije stav posunu neúplného vícebajtového znaku v parametru *mbstate.* To dává **mbrlen** schopnost restartování uprostřed vícebajtového znaku v případě potřeby, zkoumání na většině *počtu* bajtů. Pokud *mbstate* je ukazatel null, **mbrlen** používá vnitřní, statické **mbstate_t** objekt ukládat stav směny. Vzhledem k tomu, že vnitřní **mbstate_t** objekt není bezpečný pro přístup z více vláken, doporučujeme vždy přidělit a předat vlastní parametr *mbstate.*

Funkce **mbrlen** se liší od [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) svou restartovatelností. Stav shift je uložen v *mbstate* pro následná volání na stejné nebo jiné restartovatelné funkce. Výsledky nejsou definovány při míchání použití restartovatelných a nerestartovatelných funkcí.  Například aplikace by měla použít **wcsrlen** místo **wcslen,** pokud je použito následné volání **wcsrtombs** místo **wcstombs**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|nepoužije se|nepoužije se|**mbrlen**|nepoužije se|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak interpretace vícebajtových znaků závisí na aktuální znakové stránce a ukazuje schopnost obnovení **mbrlen**.

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

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
