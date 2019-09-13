---
title: scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
ms.date: 04/05/2018
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- scalblnf
- scalbnl
- scalblnl
- scalbln
- scalbn
- scalbnf
helpviewer_keywords:
- scalbn function
- scalbln function
- scalblnl function
- scalbnl function
- scalbnf function
- scalblnf function
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
ms.openlocfilehash: 794d0bdceb13aafb83de85fb29e47a4fa3125cd6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948898"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl

Vynásobí číslo s plovoucí desetinnou čárkou integrální silou FLT_RADIX.

## <a name="syntax"></a>Syntaxe

```C
double scalbn(
   double x,
   int exp
);
float scalbn(
   float x,
   int exp
);  // C++ only
long double scalbn(
   long double x,
   int exp
);  // C++ only
float scalbnf(
   float x,
   int exp
);
long double scalbnl(
   long double x,
   int exp
);
double scalbln(
   double x,
   long exp
);
float scalbln(
   float x,
   long exp
);  // C++ only
long double scalbln(
   long double x,
   long exp
);  // C++ only
float scalblnf(
   float x,
   long exp
);
long double scalblnl(
   long double x,
   long exp
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

*exp*<br/>
Celočíselný exponent.

## <a name="return-value"></a>Návratová hodnota

Funkce **scalbn –** vrací hodnotu *x* \* **FLT_RADIX**<sup>exp</sup> v případě úspěchu. Při přetečení (v závislosti na znaménku *x*) vrátí **scalbn –** +/- **HUGE_VAL**; hodnota **errno** je nastavená na **ERANGE**.

Další informace o **errno** a možných návratových hodnotách chyb naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**FLT_RADIX** je definována v \<float. h > jako nativní Číselná soustava s plovoucí desetinnou čárkou. v binárních systémech má hodnotu 2 a **scalbn –** je ekvivalentem [ldexp –](ldexp.md).

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **scalbn –** a **scalbln** , které přebírají a vracejí typ **float** nebo **Long** **Double** . V programu v jazyce C **scalbn –** vždycky přebírá **Double** a **int** a vrací **Double**a **scalbln** vždycky přebírá **Double** a **Long** a vrací hodnotu **Double**.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**scalbn –** , **scalbnf –** , **scalbnl**, **scalbln**, **scalblnf**, **scalblnl**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_scalbn.c
// Compile using: cl /W4 crt_scalbn.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 6.4, y;
   int p = 3;

   y = scalbn( x, p );
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );
}
```

### <a name="output"></a>Výstup

```Output
6.4 times FLT_RADIX to the power of 3 is 51.2
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
