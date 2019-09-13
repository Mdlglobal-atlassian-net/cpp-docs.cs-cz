---
title: div, ldiv, lldiv
ms.date: 04/05/2018
api_name:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 5b40fa0c4cc9cdf0c0de0f6af21da04b0c70369f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937691"
---
# <a name="div-ldiv-lldiv"></a>div, ldiv, lldiv

Vypočítá podíl a zbytek dvou celočíselných hodnot.

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

*numer*<br/>
Čitatel.

*denom*<br/>
Jmenovatel.

## <a name="return-value"></a>Návratová hodnota

**div** volané pomocí argumentů typu **int** vrátí strukturu typu **div_t**, která zahrnuje podíl a zbytek. Návratová hodnota s argumenty typu **Long** je **ldiv_t**a návratová hodnota s argumenty typu **Long** **Long** je **lldiv_t**. **div_t**, **ldiv_t**a **lldiv_t** jsou definovány v \<Stdlib. h >.

## <a name="remarks"></a>Poznámky

Funkce **div** rozdělí *numer* podle *denom* a vypočte podíl a zbytek. Struktura [div_t](../../c-runtime-library/standard-types.md) obsahuje podíl, **quot**a zbytek, **rem**. Znaménko podílu je stejné jako u matematického podílu. Jeho absolutní hodnota je největší celé číslo, které je menší než absolutní hodnota matematického podílu. Pokud je jmenovatel 0, program se ukončí s chybovou zprávou.

Přetížení **div** , která přijímají argumenty typu **Long** nebo **Long** **, jsou k** dispozici pouze pro C++ kód. Návratové typy [ldiv_t](../../c-runtime-library/standard-types.md) a [lldiv_t](../../c-runtime-library/standard-types.md) obsahují členy **quot** a **rem**, které mají stejný význam jako členové **div_t**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**div**, **ldiv**, **lldiv**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

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
