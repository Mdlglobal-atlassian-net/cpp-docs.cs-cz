---
title: scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
ms.date: 4/2/2020
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
- _o_scalbln
- _o_scalblnf
- _o_scalblnl
- _o_scalbn
- _o_scalbnf
- _o_scalbnl
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d0c7f6db7ad6970be85203eef76e5ccb152e2200
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332589"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl

Vynásobí číslo s plovoucí desetinnou desetinnou hodnotou integrální mocninou FLT_RADIX.

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

*X*<br/>
Hodnota s plovoucí desetinnou táceckou.

*Exp*<br/>
Integer exponent.

## <a name="return-value"></a>Návratová hodnota

**Funkce scalbn** vrátí hodnotu *x* \* **FLT_RADIX**<sup>exp</sup> při úspěchu. Při přetečení (v závislosti na znaménku *x*) **vrátí scalbn** +/- **HUGE_VAL**; hodnota **errno** je nastavena na **ERANGE**.

Další informace o **chybách** a možných hodnotách vrácení chyb naleznete [v tématu errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

**FLT_RADIX** je \<definován v float.h> jako nativní radix s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou. v binárních systémech má hodnotu 2 a **scalbn** je ekvivalentní [ldexp](ldexp.md).

Vzhledem k tomu, že C++ umožňuje přetížení, můžete volat přetížení **scalbn** a **scalbln,** které trvat a vrátit **float** nebo **dlouhé** **dvojité** typy. V programu C **scalbn** vždy trvá **double** a **int** a vrátí **double**a **scalbln** vždy trvá **dvojité** a **dlouhé** a vrátí **double**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička C|Hlavička C++|
|--------------|--------------|------------------|
|**scalbn**, **scalbnf**, **scalbnl**, **scalbln**, **scalblnf**, **scalblnl**|\<math.h>|\<cmath>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
