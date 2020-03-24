---
title: abs, labs, llabs, _abs64
ms.date: 04/05/2018
api_name:
- abs
- _abs64
- labs
- llabs
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
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
ms.openlocfilehash: a21bdbcb54d7fecf00b3c782c562d60ccc866dcc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171408"
---
# <a name="abs-labs-llabs-_abs64"></a>abs, labs, llabs, _abs64

Vypočítá absolutní hodnotu argumentu.

## <a name="syntax"></a>Syntaxe

```C
int abs( int n );
long labs( long n );
long long llabs( long long n );
__int64 _abs64( __int64 n );
```

```cpp
long abs( long n );   // C++ only
long long abs( long long n );   // C++ only
double abs( double n );   // C++ only
long double abs( long double n );   // C++ only
float abs( float n );   // C++ only
```

### <a name="parameters"></a>Parametry

*n*<br/>
Číselná hodnota.

## <a name="return-value"></a>Návratová hodnota

Funkce **ABS**, **Labs**, **LLabs** a **_abs64** vrací absolutní hodnotu parametru *n*. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení funkce **ABS** , která přijímá a vrací **dlouhé**, **dlouhé** **long**hodnoty **float**, **Double**a **Long** **Double** . Tato přetížení jsou definována v hlavičce \<cmath >. V programu v jazyce C funkce **ABS** vždycky přebírá a vrací **int**.

**Specifické pro společnost Microsoft**: vzhledem k tomu, že rozsah záporných celých čísel, která lze znázornit pomocí jakéhokoli integrálního typu, je větší než rozsah kladných celých čísel, která lze znázornit pomocí tohoto typu, je možné zadat argument pro tyto funkce, které nelze převést. Pokud absolutní hodnota argumentu nemůže být reprezentována návratovým typem, funkce **ABS** vrátí hodnotu argumentu beze změny. Konkrétně `abs(INT_MIN)` vrátí `INT_MIN`, `labs(LONG_MIN)` vrátí `LONG_MIN`, `llabs(LLONG_MIN)` vrátí `LLONG_MIN`a `_abs64(_I64_MIN)` vrátí `_I64_MIN`. To znamená, že funkce **ABS** nelze použít k zaručení kladné hodnoty.

## <a name="requirements"></a>Požadavky

|Rutina|Povinné záhlaví jazyka C|Požadovaná C++ hlavička|
|-------------|-----------------------|---------------------------|
|**ABS**, **Labs**, **LLabs**|\<Math. h > nebo \<Stdlib. h >|\<cmath >, \<cstdlib >, \<Stdlib. h > nebo \<Math. h >|
|**_abs64**|\<Stdlib. h >|\<cstdlib > nebo \<Stdlib. h >|

Chcete-li použít přetížené verze funkce **ABS** v C++, je nutné zahrnout hlavičku \<cmath >.

## <a name="example"></a>Příklad

Tento program počítá a zobrazuje absolutní hodnoty několika čísel.

```C
// crt_abs.c
// Build: cl /W3 /TC crt_abs.c
// This program demonstrates the use of the abs function
// by computing and displaying the absolute values of
// several numbers.

#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <limits.h>

int main( void )
{
    int ix = -4;
    long lx = -41567L;
    long long llx = -9876543210LL;
    __int64 wx = -1;

    // absolute 32 bit integer value
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));

    // absolute long integer value
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));

    // absolute long long integer value
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));

    // absolute 64 bit integer value
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,
        _abs64(wx));

    // Integer error cases:
    printf_s("Microsoft implementation-specific results:\n");
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));
}
```

```Output
The absolute value of -4 is 4
The absolute value of -41567 is 41567
The absolute value of -9876543210 is 9876543210
The absolute value of 0xffffffffffffffff is 0x0000000000000001
Microsoft implementation-specific results:
abs(INT_MIN) returns -2147483648
labs(LONG_MIN) returns -2147483648
llabs(LLONG_MIN) returns -9223372036854775808
_abs64(_I64_MIN) returns 0x8000000000000000
```

## <a name="see-also"></a>Viz také

[Převod dat](../../c-runtime-library/data-conversion.md)<br/>
[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[_cabs](cabs.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[imaxabs](imaxabs.md)
