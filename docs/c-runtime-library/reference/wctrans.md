---
title: wctrans
ms.date: 11/04/2016
apiname:
- wctrans
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
- wctrans
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
ms.openlocfilehash: 3c7aace7a93160d2e9a4c1523d49bcaf6ae4dc20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656687"
---
# <a name="wctrans"></a>wctrans

Určuje jednu sadu kódy znaků mapování.

## <a name="syntax"></a>Syntaxe

```C
wctrans_t wctrans(
   const char *property
);
```

### <a name="parameters"></a>Parametry

*property*<br/>
Řetězec, který určuje jeden platný transformací.

## <a name="return-value"></a>Návratová hodnota

Pokud **LC_CTYPE** kategorie aktuálního národního prostředí nedefinuje mapování, jejíž název odpovídá řetězci vlastnost *vlastnost*, vrátí funkce hodnotu nula. V opačném případě se vrací nenulovou hodnotu, vhodný pro použití jako druhý argument pro následné volání [towctrans –](towctrans.md).

## <a name="remarks"></a>Poznámky

Tato funkce určuje jednu sadu kódy znaků mapování.

Následující páry volání mají stejné chování ve všech národních prostředích, ale je možné definovat další mapování i v národním prostředí "C":

|Funkce|Stejné jako|
|--------------|-------------|
|ToLower(c)|towctrans – (c, wctrans("towlower"))|
|towupper(c)|towctrans – (c, wctrans("toupper"))|

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví|
|-------------|---------------------|
|**wctrans**|\<wctype.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_wctrans.cpp
// compile with: /EHsc
// This example determines a mapping from one set of character
// codes to another.

#include <wchar.h>
#include <wctype.h>
#include <stdio.h>
#include <iostream>

int main()
{
    wint_t c = 'a';
    printf_s("%d\n",c);

    wctrans_t i = wctrans("toupper");
    printf_s("%d\n",i);

    wctrans_t ii = wctrans("towlower");
    printf_s("%d\n",ii);

    wchar_t wc = towctrans(c, i);
    printf_s("%d\n",wc);
}
```

```Output
97
1
0
65
```

## <a name="see-also"></a>Viz také:

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
