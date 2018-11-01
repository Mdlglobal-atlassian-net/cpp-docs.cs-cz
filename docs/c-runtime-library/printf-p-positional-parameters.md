---
title: printf_p – poziční parametry
ms.date: 11/04/2016
apilocation:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
ms.openlocfilehash: 2801f1b4c61247ebb9a1402b6244f0c63c2b7dd2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498027"
---
# <a name="printfp-positional-parameters"></a>printf_p – poziční parametry

Poziční parametry umožňují určit číslo, které argumentů je nahrazena do pole v řetězci formátu. Následující poziční parametr `printf` funkce jsou k dispozici:

| Funkce bez poziční printf | Ekvivalenty pozičních parametrů více dopředu |
|---|---|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|
|[sprintf _sprintf_l –, swprintf, _swprintf_l –, \__swprintf_l –](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|
|[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|
|[vprintf, _vprintf_l, vwprintf, _vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|
|[vsprintf – _vsprintf_l –, vswprintf –, _vswprintf_l –, \__vswprintf_l –](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|

## <a name="how-to-specify-positional-parameters"></a>Jak určit poziční parametry

### <a name="parameter-indexing"></a>Parametr indexování

Ve výchozím nastavení pokud je k dispozici, žádný poziční formátování poziční funkce chovají identicky nepoziční ty. Zadejte poziční parametr formátování pomocí `%n$` na začátku specifikátor formátu, ve kterém `n` je pozice parametru pro formátování v seznamu parametrů. Pozice parametru začíná 1 pro první argument po formátovací řetězec. Zbývající část specifikátoru formátu následuje stejná pravidla jako `printf` specifikátorem formátu. Další informace o formátu specfiers najdete v tématu [syntaxe specifikace formátu: funkce printf a wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

Tady je příklad poziční formátování:

```C
_printf_p("%1$s %2$s", "November", "10");
```

Vytiskne toto:

```
November 10
```

Pořadí čísel používá nemusí odpovídat pořadí argumentů. Například je platným formátovacím řetězcem:

```C
_printf_p("%2$s %1$s", "November", "10");
```

Vytiskne toto:

```
10 November
```

Na rozdíl od tradičních formátovací řetězce poziční parametry lze více než jednou v řetězci formátu. Například

```C
_printf_p("%1$d times %1$d is %2$d", 10, 100);
```

Vytiskne toto:

```
10 times 10 is 100
```

Všechny argumenty musí využívat alespoň jednou někde ve formátovacím řetězci. Maximální počet povolený v řetězci formátu poziční parametry je dán `_ARGMAX`.

### <a name="width-and-precision"></a>Šířka a přesnost

Můžete použít `*n$` určit poziční parametr jako specifikátor šířku nebo přesnosti, kde `n` je parametr width nebo přesnosti pozice v seznamu parametrů. Pozice hodnotu šířky nebo přesnosti musí být uvedena ihned následující \* symbol. Například

```C
_printf_p("%1$*2$s","Hello", 10);
```

or

```C
_printf_p("%2$*1$s", 10, "Hello");
```

### <a name="mixing-positional-and-non-positional-arguments"></a>Kombinování poziční a nepoziční argumenty

Poziční parametry nelze kombinovat s – poziční parametry ve stejném formátovacím řetězci. Pokud poziční formátování se používá, musí všechny specifikátory formátu použít poziční formátování. Ale `printf_p` a související funkce stále podporovat – poziční parametry ve formátu řetězců obsahující žádné poziční parametry.

## <a name="example"></a>Příklad

```C
// positional_args.c
// Build by using: cl /W4 positional_args.c
// Positional arguments allow the specification of the order
// in which arguments are consumed in a formatting string.

#include <stdio.h>

int main()
{
    int     i = 1,
            j = 2,
            k = 3;
    double  x = 0.1,
            y = 2.22,
            z = 333.3333;
    char    *s1 = "abc",
            *s2 = "def",
            *s3 = "ghi";

    // If positional arguments are unspecified,
    // normal input order is used.
    _printf_p("%d %d %d\n", i, j, k);

    // Positional arguments are numbers followed by a $ character.
    _printf_p("%3$d %1$d %2$d\n", i, j, k);

    // The same positional argument may be reused.
    _printf_p("%1$d %2$d %1$d\n", i, j);

    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);

    // Precision and width specifiers must be int types.
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);
}
```

```Output
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```

## <a name="see-also"></a>Viz také

[Syntaxe specifikace formátu: funkce printf a wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)