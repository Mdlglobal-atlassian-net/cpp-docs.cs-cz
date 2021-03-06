---
title: expm1, expm1f, expm1l
ms.date: 04/05/2018
api_name:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 77bd44975e97cc646f7d2fd100d86b6661b8c2e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941536"
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Vypočítá exponenciální hodnotu v hodnotě, která je odečtena od hodnoty 1.

## <a name="syntax"></a>Syntaxe

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Exponenciální hodnota s plovoucí desetinnou čárkou.

## <a name="return-value"></a>Návratová hodnota

Funkce **expm1 –** vrací hodnotu s plovoucí desetinnou čárkou, která představuje e<sup>x</sup> -1, pokud je úspěšná. Při přetečení vrátí **expm1 –** hodnotu **HUGE_VAL**, **expm1f –** vrátí **HUGE_VALF**, **expm1l** vrátí **HUGE_VALL**a **errno** je nastaven na **ERANGE**. Další informace o návratových kódech naleznete v tématu [errno, _doserrno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **expm1 –** , která přijímají a vracejí hodnoty **float** a **Long** **Double** . V programu v jazyce C **expm1 –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**expm1 –** , **expm1f –** , **expm1l**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
