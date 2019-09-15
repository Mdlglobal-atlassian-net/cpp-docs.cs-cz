---
title: wctrans
ms.date: 11/04/2016
api_name:
- wctrans
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
- wctrans
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
ms.openlocfilehash: a75de3b699d0eb5ec6117d0f627e6a8ba34dbc62
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944878"
---
# <a name="wctrans"></a>wctrans

Určuje mapování jedné sady kódů znaků na jinou.

## <a name="syntax"></a>Syntaxe

```C
wctrans_t wctrans(
   const char *property
);
```

### <a name="parameters"></a>Parametry

*property*<br/>
Řetězec, který určuje jednu z platných transformací.

## <a name="return-value"></a>Návratová hodnota

Pokud kategorie **LC_CTYPE** aktuálního národního prostředí nedefinuje mapování, jehož název odpovídá *vlastnosti*řetězce vlastnosti, vrátí funkce hodnotu nula. V opačném případě vrátí nenulovou hodnotu vhodnou pro použití jako druhý argument u následného volání [towctrans](towctrans.md).

## <a name="remarks"></a>Poznámky

Tato funkce Určuje mapování z jedné sady kódů znaků na jinou.

Následující páry volání mají stejné chování ve všech národních prostředích, ale je možné definovat další mapování i v národním prostředí "C":

|Funkce|Stejné jako|
|--------------|-------------|
|ToLower (c)|towctrans (c; wctrans ("towlower"))|
|towupper (c)|towctrans (c; wctrans ("ToUpper"))|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaná hlavička|
|-------------|---------------------|
|**wctrans**|\<wctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
