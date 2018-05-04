---
title: modf – modff –, modfl | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
dev_langs:
- C++
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87cddb8b565cdc369e6b1e9679583db64039bb49
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="modf-modff-modfl"></a>modf – modff –, modfl

Rozdělí do desetinnou hodnotu s plovoucí desetinnou čárkou a částí celé číslo.

## <a name="syntax"></a>Syntaxe

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

*IntPtr*<br/>
Ukazatel na uložené celočíselnou část.

## <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí podepsaný zlomkové části *x*. Neexistuje žádný návratový chyby.

## <a name="remarks"></a>Poznámky

**Modf –** funkce rozdělení s plovoucí desetinnou čárkou *x* do zlomkové části celé číslo, z nichž každá má stejné znaménko jako a *x*. Podepsaný zlomkové části *x* je vrácen. Celočíselnou část je uložený jako hodnotu s plovoucí desetinnou čárkou v *intptr*.

**modf –** má implementace, která používá Streaming SIMD Extensions 2 (SSE2). V tématu [_set_sse2_enable –](set-sse2-enable.md) informace a omezení používání SSE2 implementace.

C++ umožňuje přetížení, takže můžete volat přetížení **modf –** , přijmout a vrátit **float** nebo **dlouho** **dvojité** parametry. V programu C **modf –** vždy má dvě hodnoty double a vrátí hodnotu double.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**modf –**, **modff –**, **modfl**|C: \<math.h ><br /><br /> C++:, \<cmath – > nebo \<math.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
