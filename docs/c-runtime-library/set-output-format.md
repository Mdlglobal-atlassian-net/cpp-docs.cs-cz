---
title: _set_output_format
ms.date: 11/04/2016
api_name:
- _set_output_format
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_output_format
- _set_output_format
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
ms.openlocfilehash: c855df4c29a53fd898b920f6446afe4e568ba5bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360923"
---
# <a name="_set_output_format"></a>_set_output_format

Přizpůsobí výstupní formáty používané formátované vstupně-výstupními funkcemi.

> [!IMPORTANT]
> Tato funkce je zastaralá. Počínaje Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>Parametry

*Formát*<br/>
[v] Hodnota představující formát, který chcete použít.

## <a name="return-value"></a>Návratová hodnota

Předchozí výstupní formát.

## <a name="remarks"></a>Poznámky

`_set_output_format`slouží ke konfiguraci výstupu formátovaných vstupně-výstupních funkcí, jako je [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). V současné době je jedinou konvencí formátování, kterou lze změnit touto funkcí, počet číslic zobrazených v exponentech ve výstupu čísel s plovoucí desetinnou položkou.

Ve výchozím nastavení vytiskne výstup `printf_s`čísel `wprintf_s`s plovoucí desetinnou úseček podle funkcí, jako je například , , a související funkce v knihovně Visual C++ Standard C tři číslice pro exponent, i když tři číslice nejsou nutné k reprezentaci hodnoty exponentu. Nuly se používají k vyložce hodnoty na tři číslice. `_set_output_format`umožňuje změnit toto chování tak, aby v exponentu byly vytištěny pouze dvě číslice, pokud není třetí číslice vyžadována velikostí exponentu.

Chcete-li povolit dvoumístné exponenty, `_TWO_DIGIT_EXPONENT`zavolejte tuto funkci s parametrem , jak je znázorněno v příkladu. Chcete-li zakázat dvoumístné exponenty, zavolejte tuto funkci s argumentem 0.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../c-runtime-library/compatibility.md) v úvodu.

## <a name="example"></a>Příklad

```C
// crt_set_output_format.c
#include <stdio.h>

void printvalues(double x, double y)
{
   printf_s("%11.4e %11.4e\n", x, y);
   printf_s("%11.4E %11.4E\n", x, y);
   printf_s("%11.4g %11.4g\n", x, y);
   printf_s("%11.4G %11.4G\n", x, y);
}

int main()
{
   double x = 1.211E-5;
   double y = 2.3056E-112;
   unsigned int old_exponent_format;

   // Use the default format
   printvalues(x, y);

   // Enable two-digit exponent format
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);

   printvalues(x, y);

   // Disable two-digit exponent format
   _set_output_format( old_exponent_format );

   printvalues(x, y);
}
```

```Output
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
1.2110e-05 2.3056e-112
1.2110E-05 2.3056E-112
  1.211e-05  2.306e-112
  1.211E-05  2.306E-112
1.2110e-005 2.3056e-112
1.2110E-005 2.3056E-112
1.211e-005  2.306e-112
1.211E-005  2.306E-112
```

## <a name="see-also"></a>Viz také

[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
