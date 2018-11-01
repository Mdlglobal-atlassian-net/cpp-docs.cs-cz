---
title: fabs – fabsf –, fabsl
ms.date: 04/05/2018
apiname:
- fabsf
- fabs
- fabsl
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: 8df36c06fb3ca9af9be4cf704998946b3eaf9a6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623558"
---
# <a name="fabs-fabsf-fabsl"></a>fabs – fabsf –, fabsl

Vypočítá absolutní hodnotu argumentu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**Fabs –** funkce vrátí absolutní hodnotu argumentu *x*. Není vrácena žádná chyba.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|ROZMEZÍ QNAN, AJÍT|žádná|_DOMÉNA|

## <a name="remarks"></a>Poznámky

Jazyk C++ umožňuje přetížení, takže můžete volat přetížení **fabs –** zadáte-li \<cmath > záhlaví. V programu jazyka C **fabs –** vždy převezme a vrátí **double**.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaná hlavička C|Požadované hlaviček jazyka C++|
|--------------|-----------------------|---------------------------|
|**fabs –**, **fabsf –**, **fabsl**|\<Math.h >|\<cmath > nebo \<math.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad pro [abs](abs-labs-llabs-abs64.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
