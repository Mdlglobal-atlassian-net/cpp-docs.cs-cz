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
ms.openlocfilehash: b67abb58f4d62c7c54b61d1b1699f09c1bd51b40
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957315"
---
# <a name="_set_output_format"></a>_set_output_format

Přizpůsobí výstupní formáty používané ve formátovaných vstupně-výstupních funkcích.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Počínaje verzí Visual Studio 2015 není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
unsigned int _set_output_format(
   unsigned int format
);
```

#### <a name="parameters"></a>Parametry

*format*<br/>
pro Hodnota, která představuje formát, který má být použit.

## <a name="return-value"></a>Návratová hodnota

Předchozí výstupní formát.

## <a name="remarks"></a>Poznámky

`_set_output_format`slouží ke konfiguraci výstupu formátovaných vstupně-výstupních funkcí, jako je [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). V současné době jediná konvence formátování, kterou lze změnit pomocí této funkce, je počet číslic zobrazených v exponentech ve výstupu čísel s plovoucí desetinnou čárkou.

Ve výchozím nastavení výstupy čísel s plovoucí desetinnou čárkou podle `printf_s`funkcí `wprintf_s`, jako je, a související funkce C++ v knihovně jazyka Visual Standard jazyka C, tisknou tři číslice pro exponent, i když tři číslice nejsou požadovány pro reprezentaci hodnoty exponent. K vyplnění hodnoty třemi číslicemi se používají nuly. `_set_output_format`umožňuje změnit toto chování tak, aby se na exponent tiskly jenom dvě číslice, pokud velikost exponentu nepožaduje třetí číslice.

Chcete-li povolit dvojúrovňové exponenty, zavolejte tuto funkci s parametrem `_TWO_DIGIT_EXPONENT`, jak je znázorněno v příkladu. Chcete-li zakázat dvě exponenty číslic, zavolejte tuto funkci s argumentem 0.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_set_output_format`|\<stdio.h>|

Další informace o kompatibilitě naleznete v úvodu v tématu [Kompatibilita](../c-runtime-library/compatibility.md) .

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

## <a name="see-also"></a>Viz také:

[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[_get_output_format](../c-runtime-library/get-output-format.md)
