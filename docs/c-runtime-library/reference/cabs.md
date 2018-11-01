---
title: _cabs
ms.date: 11/04/2016
apiname:
- _cabs
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
- cabsl
- _cabs
- _cabsl
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 3e95b6f568ce66b8e9e5483bd1dcbcfaa7af3d28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645806"
---
# <a name="cabs"></a>_cabs

Vypočítá absolutní hodnotu komplexního čísla.

## <a name="syntax"></a>Syntaxe

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní čísla.

## <a name="return-value"></a>Návratová hodnota

**_cabs** vrátí absolutní hodnotu svého argumentu, pokud je úspěšná. Při přetečení **_cabs** vrátí **HUGE_VAL** a nastaví **errno** k **ERANGE**. Můžete změnit zpracování chyb pomocí [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

**_Cabs** funkce vypočítá absolutní hodnotu komplexního čísla, která musí být strukturu typu [_complex](../../c-runtime-library/standard-types.md). Struktura *z* se skládá z proceduru reálnou součástí *x* a imaginární části *y*. Volání **_cabs** produkuje hodnotu ekvivalentní výraz `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_cabs**|\<Math.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)