---
title: mbrlen
ms.date: 11/04/2016
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: ec9079b9b164e2b609a956ddf3a75cd42923bafc
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518330"
---
# <a name="mbrlen"></a>mbrlen

Určete počet bajtů, které jsou vyžadovány k dokončení vícebajtového znaku v aktuálním národním prostředí, pomocí funkce restartování uprostřed vícebajtového znaku.

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
Ukazatel na další bajt ke kontrole ve vícebajtovém znakovém řetězci.

*Počet*<br/>
Maximální počet bajtů ke kontrole.

*mbstate*<br/>
Ukazatel na aktuální stav shift úvodní bajt *str*.

## <a name="return-value"></a>Návratová hodnota

Jeden z následujících hodnot:

|||
|-|-|
0|Další *počet* nebo menší počet bajtů dokončení vícebajtového znaku, který představuje širokého znaku null.
1 *počet*včetně|Další *počet* nebo menší počet bajtů je platný vícebajtový znak. Vrácená hodnota je počet bajtů, které dokončení vícebajtového znaku.
(size_t) -(2)|Další *počet* bajtů přispívat k neúplný, ale potenciálně platný vícebajtový znak a ke všem *počet* byly zpracovány bajtů.
(size_t) (-1)|Došlo k chybě kódování. Další *počet* nebo menší počet bajtů se nepodílejí na dokončení a je platný vícebajtový znak. V takovém případě **errno** je nastavena na EILSEQ a stav převodu v *mbstate* není zadána.

## <a name="remarks"></a>Poznámky

**Mbrlen –** funkce zkontroluje maximálně *počet* bajtů počínaje bajt odkazované *str* k určení počtu bajtů, které jsou vyžadovány k dokončení následujících vícebajtový znak, včetně nějaké sekvence shift. Je ekvivalentní volání `mbrtowc(NULL, str, count, &mbstate)` kde *mbstate* je buď uživatelem zadaného **mbstate_t** , nebo statické vnitřní objekt poskytovaných knihovnou.

**Mbrlen –** funkce uloží a použije shift stavu nedokončené vícebajtového znaku v *mbstate* parametru. Díky tomu **mbrlen –** schopnost restartování uprostřed vícebajtového znaku, pokud je třeba, zkoumání maximálně *počet* bajtů. Pokud *mbstate* je ukazatel s hodnotou null, **mbrlen –** používá interní statické **mbstate_t** objekt pro uložení stavu shift. Protože vnitřní **mbstate_t** objektu není bezpečná pro vlákno, doporučujeme, abyste vždy přidělení a předání vlastní *mbstate* parametru.

**Mbrlen –** funkce se liší od [_mbclen mblen –, _mblen_l –](mbclen-mblen-mblen-l.md) podle jeho restartability. Stav shift je uložený ve službě *mbstate* pro pozdější volání na stejné nebo jiné funkce nabízet možnost restartování. Při použití funkcí restartovatelnou službu a nonrestartable případě nejsou výsledky definovány.  Například by měla aplikace použít **wcsrlen** místo **wcslen –** Pokud následných volání **wcsrtombs –** se použije namísto **wcstombs –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|Není k dispozici|Není k dispozici|**mbrlen**|Není k dispozici|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak výklad vícebajtových znaků závisí na aktuální znakové stránce a demonstruje schopnosti produktu obnovení **mbrlen –**.

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

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
