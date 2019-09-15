---
title: wctob
ms.date: 11/04/2016
api_name:
- wctob
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 151325b0d66e6d57156cdf94828ca1d4b151d437
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944929"
---
# <a name="wctob"></a>wctob

Určuje, zda velký znak odpovídá vícebajtovým znakům a vrací jeho vícebajtovou reprezentaci znaků.

## <a name="syntax"></a>Syntaxe

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parametry

*wchar*<br/>
Hodnota, která se má přeložit

## <a name="return-value"></a>Návratová hodnota

Pokud **wctob** úspěšně převede velký znak, vrátí jeho revícebajtovou reprezentaci pouze v případě, že vícebajtový znak je přesně jeden bajt dlouhý. Pokud **wctob** narazí na velký znak, nelze převést na vícebajtový znak nebo vícebajtový znak není přesně 1 bajtem a vrátí hodnotu-1.

## <a name="remarks"></a>Poznámky

Funkce **wctob** převede velký znak obsažený v *WCHAR* na odpovídající vícebajtový znak předaný návratovou hodnotou **int** , pokud je vícebajtový znak v jednom bajtu dlouhý.

Pokud **wctob** nebylo úspěšné a nebyl nalezen žádný odpovídající vícebajtový znak, funkce nastaví **errno** na **EILSEQ** a vrátí-1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program ilustruje chování funkce **wcstombs** .

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
