---
title: copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl
ms.date: 04/05/2018
api_name:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 1575f0863b56256513cf6a93cf7b63f3d921af57
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942857"
---
# <a name="copysign-copysignf-copysignl-_copysign-_copysignf-_copysignl"></a>copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl

Vrátí hodnotu, která má velikost jednoho argumentu a znaménko jiného.

## <a name="syntax"></a>Syntaxe

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou, která je vrácena jako velikost výsledku.

*y*<br/>
Hodnota s plovoucí desetinnou čárkou, která je vrácena jako znaménko výsledku.

[Rutiny podpory plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>Návratová hodnota

Funkce **copysign –** vrací hodnotu s plovoucí desetinnou čárkou, která kombinuje velikost *x* a znaménko *y*. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **copysign –** , která přijímají a vracejí hodnoty **float** nebo **Long** **Double** . V programu v jazyce C **copysign –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_copysign**|\<float. h >|
|**copysign**, **copysignf**, **copysignl**, **_copysignf**, **_copysignl**|\<Math. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign, _chgsignf, _chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
