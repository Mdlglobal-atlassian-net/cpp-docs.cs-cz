---
title: wctob – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wctob
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctob
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1cff2dcb8d6b0ad3756a8a0047fcc9b982fb7bb8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="wctob"></a>wctob

Určuje, jestli široká znaková odpovídá vícebajtových znaků a vrátí její reprezentace vícebajtových znaků.

## <a name="syntax"></a>Syntaxe

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parametry

*wchar*<br/>
Hodnota přeložit.

## <a name="return-value"></a>Návratová hodnota

Pokud **wctob –** úspěšně převede široká znaková vrátí jeho reprezentace vícebajtových znaků, pouze pokud je přesně jeden bajt vícebajtových znaků. Pokud **wctob –** komunikaci široké nelze převést na vícebajtových znaků nebo vícebajtových znaků je znak přesně jeden bajt dlouhý, vrátí hodnotu -1.

## <a name="remarks"></a>Poznámky

**Wctob –** funkce převede široká znaková obsažené v *wchar* na odpovídající vícebajtových znaků předaná návratový **int** hodnotu, pokud vícebajtových znak, který je právě jeden bajt.

Pokud **wctob –** nebylo úspěšné, ale nebyl nalezen žádný odpovídající vícebajtových znaků, funkce nastaví **errno** k **eilseq –** a vrátí hodnotu -1.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Tento program znázorňuje chování **wcstombs –** funkce.

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

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
