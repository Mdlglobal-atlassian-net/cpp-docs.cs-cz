---
title: _scalb, _scalbf
ms.date: 04/05/2018
api_name:
- _scalb
- _scalbf
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
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
ms.openlocfilehash: 630a5e3db2c39cb40d31c71e6a6dfa214ed91e34
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948887"
---
# <a name="_scalb-_scalbf"></a>_scalb, _scalbf

Škáluje argument mocninou mocniny 2.

## <a name="syntax"></a>Syntaxe

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Dvojitá přesnost, hodnota s plovoucí desetinnou čárkou.

*exp*<br/>
Celočíselný Exponent typu Long.

## <a name="return-value"></a>Návratová hodnota

Vrátí exponenciální hodnotu, pokud je úspěšná. Při přetečení (v závislosti na znaménku *x*) vrátí **_scalb** +/- **HUGE_VAL**; proměnná **errno** je nastavená na **ERANGE**.

Další informace o tomto a dalších návratových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Funkce **_scalb** vypočítá hodnotu *x* \* 2<sup>*exp*</sup>.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_scalb**, **_scalbf**|\<float. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
