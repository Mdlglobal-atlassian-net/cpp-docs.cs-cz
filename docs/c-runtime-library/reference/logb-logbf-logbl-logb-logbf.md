---
title: logb, logbf, logbl, _logb, _logbf
ms.date: 04/05/2018
apiname:
- logb
- _logb
- _logbl
- logbf
- logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
ms.openlocfilehash: 9f598eedaf30b1f2a1858129e648a117355d112e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466284"
---
# <a name="logb-logbf-logbl-logb-logbf"></a>logb, logbf, logbl, _logb, _logbf

Extrahuje hodnotu exponentu argumentu s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

**logb –** vrací hodnotu nevyváženého exponentu *x* jako celé číslo se znaménkem reprezentována jako hodnotu s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

**Logb –** funkce extrahují exponenciální hodnotu argument s plovoucí desetinnou čárkou *x*, jako by šlo *x* byly zastoupeny s nekonečným rozsahem. Pokud argument *x* je denormalizovaný, je zacházeno, jako kdyby byl normalizován.

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **logb –** , která používají a vrací **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **logb –** vždy převezme a vrátí **double**.

|Vstup|Výjimka SEH|Výjimka Matherr|
|-----------|-------------------|-----------------------|
|ROZMEZÍ QNAN, AJÍT|Žádné|_DOMÉNA|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_logb**|\<float.h >|
|**logb –**, **logbf –**, **logbl –**, **_logbf –**|\<Math.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
