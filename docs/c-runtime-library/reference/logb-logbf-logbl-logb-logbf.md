---
title: logb, logbf, logbl, _logb, _logbf
ms.date: 04/05/2018
api_name:
- logb
- _logb
- _logbl
- logbf
- logbl
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
ms.openlocfilehash: c5fc59f786b00dcf4ab1056424d8442a03f3adbf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953155"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>logb, logbf, logbl, _logb, _logbf

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

**logb –** vrací hodnotu neposunutého exponentu *x* jako celé číslo se znaménkem, které je reprezentované jako hodnota s plovoucí desetinnou čárkou.

## <a name="remarks"></a>Poznámky

Funkce **logb –** extrahuje exponenciální hodnotu argumentu s plovoucí desetinnou čárkou *x*, jako kdyby byl znak *x* reprezentován nekonečným rozsahem. Pokud je argument *x* denormalizovaný, je považován za normalizovaný.

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **logb –** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **logb –** vždycky přebírá a vrací **Double**.

|Vstup|Výjimka SEH|Výjimka matherr|
|-----------|-------------------|-----------------------|
|QNAN, ZASÁHNOUT|Žádné|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_logb**|\<float. h >|
|**logb**, **logbf**, **logbl**, **_logbf**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
