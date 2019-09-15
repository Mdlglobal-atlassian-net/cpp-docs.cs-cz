---
title: _get_output_format
ms.date: 11/04/2016
api_name:
- _get_output_format
api_location:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_output_format
- _get_output_format
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
ms.openlocfilehash: 20afa988bc4fdf3bc3a6ff073a48a1cc00ff84c5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944357"
---
# <a name="_get_output_format"></a>_get_output_format

Získá aktuální hodnotu příznaku výstupního formátu.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Počínaje verzí Visual Studio 2015 není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Návratová hodnota

Aktuální hodnota příznaku výstupního formátu.

## <a name="remarks"></a>Poznámky

Příznak výstupní formát ovládá funkce formátovaného vstupu a výstupu. Příznak má v současnosti dvě možné hodnoty: 0 a `_TWO_DIGIT_EXPONENT`. Je `_TWO_DIGIT_EXPONENT` -li nastavena hodnota, čísla s plovoucí desetinnou čárkou budou vytištěna pouze pomocí dvou číslic ve exponentu, pokud velikost exponentu nepožaduje třetí číslice. Pokud je příznak nula, zobrazí výstup plovoucí desetinné čárky tři číslice exponentu, pokud je to nutné k vyplnění hodnoty třemi číslicemi.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Další informace o kompatibilitě naleznete v úvodu v tématu [Kompatibilita](../c-runtime-library/compatibility.md) .

## <a name="see-also"></a>Viz také:

[Syntaxe specifikace formátu: funkce printf a wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)
