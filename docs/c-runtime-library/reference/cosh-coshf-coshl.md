---
title: COSH – coshf –, coshl –
ms.date: 04/11/2018
apiname:
- cosh
- coshf
- coshl
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: 0f55e084e760cb6d04dbe7ec4fefb5e2ac1d79fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609531"
---
# <a name="cosh-coshf-coshl"></a>COSH – coshf –, coshl –

Vypočte hyperbolický kosinus.

## <a name="syntax"></a>Syntaxe

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Úhel v radiánech.

## <a name="return-value"></a>Návratová hodnota

Hyperbolický kosinus *x*.

Ve výchozím nastavení, pokud je výsledek příliš velké **cosh**, **coshf –**, nebo **coshl –** volání funkce vrátí **HUGE_VAL** a nastaví **errno** k **ERANGE**.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|ROZMEZÍ **QNAN**, **AJÍT**|žádná|**_DOMÉNA**|
|*x* ≥ 7.104760e + 002|**NEPŘESNÉ**+**PŘETEČENÍ**|**PŘETEČENÍ**|

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **cosh** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **cosh** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadované záhlaví (C)|Požadované záhlaví (C++)|
|-------------|---------------------|-|
|**coshf –**, **cosl –**, **coshl –**|\<Math.h >|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [sinh sinhf –, sinhl –](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
