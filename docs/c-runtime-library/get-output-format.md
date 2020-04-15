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
ms.openlocfilehash: 682ab9796942e52ed036193887158ea22b738189
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349337"
---
# <a name="_get_output_format"></a>_get_output_format

Získá aktuální hodnotu příznaku výstupního formátu.

> [!IMPORTANT]
> Tato funkce je zastaralá. Počínaje Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
unsigned int _get_output_format();
```

## <a name="return-value"></a>Návratová hodnota

Aktuální hodnota příznaku výstupního formátu.

## <a name="remarks"></a>Poznámky

Příznak výstupního formátu řídí funkce formátovaných vstupně-výstupních výstupů. V současné době má příznak dvě `_TWO_DIGIT_EXPONENT`možné hodnoty: 0 a . Pokud `_TWO_DIGIT_EXPONENT` je nastavena, čísla s plovoucí desetinnou desetinnou desetinnou třídou jsou vytištěna pouze se dvěma číslicemi v exponentu, pokud není třetí číslice vyžadována velikostí exponentu. Pokud je příznak nula, výstup s plovoucí desetinnou desetinnou desetinnou desetinnou tištěnou se zobrazí tři číslice exponentu, v případě potřeby pomocí nul, aby se hodnota vyložce nepoužívala na tři číslice.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_get_output_format`|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md) v úvodu.

## <a name="see-also"></a>Viz také

[Syntaxe specifikace formátu: printf a wprintf Functions](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_set_output_format](../c-runtime-library/set-output-format.md)
