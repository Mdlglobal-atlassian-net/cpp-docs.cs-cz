---
title: mbrlen – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77e5cb106a971bcaf02662bfd8459267a134173a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404438"
---
# <a name="mbrlen"></a>mbrlen

Určete počet bajtů, které jsou nutné k dokončení vícebajtových znaků v aktuální národní prostředí, pomocí funkce restartování uprostřed vícebajtových znaků.

## <a name="syntax"></a>Syntaxe

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Ukazatel na další bajtů, chcete-li prověřit řetězce vícebajtových znaků.

*Počet*<br/>
Maximální počet bajtů ke kontrole.

*mbstate*<br/>
Ukazatel na aktuální stav shift počáteční bajt *str*.

## <a name="return-value"></a>Návratová hodnota

Jedna z následujících hodnot:

|||
|-|-|
0|Další *počet* nebo méně bajtů dokončení vícebajtových znaků, která představuje celou znak hodnoty null.
1 *počet*(včetně)|Další *počet* nebo méně bajtů dokončení platný vícebajtových znaků. Hodnota vrácená je počet bajtů, která dokončí vícebajtových znaků.
size_t (–) -(2)|Další *počet* bajtů přispívat do neúplné ale potenciálně platný vícebajtových znaků a všechny *počet* bajtů byly zpracovány.
size_t (–) (-1)|Došlo k chybě kódování. Další *počet* nebo méně bajtů nepřispívají k dokončení a platné vícebajtových znaků. V takovém případě **errno** je nastavena na eilseq – a stav převodu v *mbstate* není zadáno.

## <a name="remarks"></a>Poznámky

**Mbrlen –** funkce zkontroluje maximálně *počet* bajtů počínaje bajtů na kterou odkazuje *str* můžete určit počet bajtů, které jsou nutné k dokončení další vícebajtových znaků, včetně jakýchkoli pořadí shift. Ta je ekvivalentní volání `mbrtowc(NULL, str, count, &mbstate)` kde *mbstate* je buď zadaný uživatelem **mbstate_t** objekt nebo statické vnitřní objekt Poskytnutý knihovny.

**Mbrlen –** funkce uloží a používá shift stav nekompletní vícebajtových znaků v *mbstate* parametr. Díky tomu **mbrlen –** schopnosti produktu restartováním uprostřed vícebajtových znaků, pokud se potřeby zkoumání maximálně *počet* bajtů. Pokud *mbstate* je ukazatel s hodnotou null, **mbrlen –** používá interní statická **mbstate_t** objekt pro uložení stavu shift. Protože interní **mbstate_t** objekt není bezpečné pro přístup z více vláken, doporučujeme, abyste vždy přidělit a předat vlastní *mbstate* parametr.

**Mbrlen –** funkce se liší od [_mbclen, mblen –, _mblen_l –](mbclen-mblen-mblen-l.md) podle jeho restartability. Stav posunutí je uložený ve *mbstate* pro následující volání stejné nebo jiné funkce nabízet možnost restartování. Výsledky nejsou definovány při kombinování použití funkce nonrestartable a nabízet možnost restartování.  Například by měla použít aplikace **wcsrlen** místo **wcslen –** Pokud následných volání **wcsrtombs –** se používá místo **wcstombs –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|Není k dispozici|Není k dispozici|**mbrlen**|Není k dispozici|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak se výklad více-bajtové znaky závisí na aktuální stránce kódu a ukazuje, opětovné funkce **mbrlen –**.

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
