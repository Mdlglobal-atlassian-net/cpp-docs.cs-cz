---
title: _get_output_format
ms.date: 11/04/2016
apiname:
- _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
ms.openlocfilehash: 60e209f6f8b723bfae1a4b434750b6237dc6479d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751424"
---
# <a name="getoutputformat"></a>_get_output_format

Získá aktuální hodnotu příznaku formát výstupu.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Od v sadě Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Návratová hodnota

Aktuální hodnota příznaku formát výstupu.

## <a name="remarks"></a>Poznámky

Příznak výstupního formát řídí funkce formátovaný vstup/výstup. V současné době nemá příznak dvě možné hodnoty: 0 a `_TWO_DIGIT_EXPONENT`. Pokud `_TWO_DIGIT_EXPONENT` je nastavena plovoucí desetinnou čárkou se vytiskne pouze dvě číslice v exponentu Pokud třetí číslici vyžaduje velikost exponent. Pokud příznak je nula, plovoucí desetinnou čárkou výstupu zobrazí tři číslic exponentu, pomocí nuly v případě potřeby pro vyplnění hodnota, která má tři číslice.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md) v úvodu.

## <a name="see-also"></a>Viz také:

[Syntaxe specifikace formátu: funkce printf a wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)
