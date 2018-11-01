---
title: div, ldiv, lldiv
ms.date: 04/05/2018
apiname:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 0ee1b3b6a5d7b15470ffe1e667b4077d1f9581e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653424"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

Počítá podíl a zbytek dvou celočíselných hodnot.

## <a name="syntax"></a>Syntaxe

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>Parametry

*počet*<br/>
Čítač.

*denom*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

**div** volaná pomocí argumentů typu **int** vrátí strukturu typu **div_t**, která zahrnuje podíl a zbytek. Návratová hodnota s argumenty typu **dlouhé** je **ldiv_t**a návratová hodnota s argumenty typu **dlouhé** **dlouhé** je **lldiv_t**. **div_t**, **ldiv_t**, a **lldiv_t** jsou definovány v \<stdlib.h >.

## <a name="remarks"></a>Poznámky

**Div** funkce rozdělí *číslo* podle *denom* a tím počítá podíl a zbytek. [Div_t](../../c-runtime-library/standard-types.md) struktura obsahuje podíl, **quot**a zbytek **rem**. Znaménko podílu je stejné jako matematický podíl. Jeho absolutní hodnota je největší celé číslo menší než absolutní hodnota matematického podílu. Je-li jmenovatelem 0, program se ukončí s chybovou zprávou.

Přetížení **div** , která přijímají argumenty typu **dlouhé** nebo **dlouhé** **dlouhé** jsou dostupné pouze pro kód jazyka C++. Návratové typy [ldiv_t](../../c-runtime-library/standard-types.md) a [lldiv_t](../../c-runtime-library/standard-types.md) obsahuje členy **quot** a **rem**, které mají stejný význam jako členové **div_t**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv, lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
