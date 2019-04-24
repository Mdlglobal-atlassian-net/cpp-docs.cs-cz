---
title: frexp – frexpf –, frexpl –
ms.date: 04/05/2018
apiname:
- frexp
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: c9e259f730d2d63d07032735be930f6f0fdb17e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62332972"
---
# <a name="frexp-frexpf-frexpl"></a>frexp – frexpf –, frexpl –

Načte mantisu a exponent čísla s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

*expptr*<br/>
Ukazatel na exponent uložené celé číslo.

## <a name="return-value"></a>Návratová hodnota

**frexp –** vrátí mantisa. Pokud *x* je 0, funkce vrátí 0 pro mantisu a exponent. Pokud *expptr* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí hodnotu 0.

## <a name="remarks"></a>Poznámky

**Frexp –** funkce rozdělí hodnotu s plovoucí desetinnou čárkou (*x*) do mantisy (*m*) a exponent (*n*), tak, aby absolutní Hodnota *m* je větší než nebo rovna hodnotě 0,5 a nižší než 1.0, a *x* = *m* * 2<sup>*n*</sup>. Celé číslo exponent *n* je uložen v umístění, na které odkazuje *expptr*.

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **frexp –**. V programu jazyka C **frexp –** vždy přijímá **double** a **int** ukazatele a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**frexp –**, **frexpf –**, **frexpl –**|\<math.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
