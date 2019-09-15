---
title: fmin, fminf, fminl
ms.date: 04/05/2018
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: df01f2205291920b8c0519db622c93048278beb1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957092"
---
# <a name="fmin-fminf-fminl"></a>fmin, fminf, fminl

Určuje menší ze dvou zadaných hodnot.

## <a name="syntax"></a>Syntaxe

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
První hodnota pro porovnání.

*y*<br/>
Druhá hodnota pro porovnání.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí menší hodnoty *x* nebo *y*.

|Vstup|Výsledek|
|-----------|------------|
|*x* je NaN|*y*|
|*y* je NaN|*x*|
|*x* a *y* jsou NaN.|NaN|

Funkce nezpůsobí vyvolání [_matherr](matherr.md) , způsobují výjimky s plovoucí desetinnou čárkou nebo mění hodnotu **errno**.

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **fmin –** , která přijímají a vracejí typ **float** a **Long** **Double** . V programu v jazyce C **fmin –** vždycky přebírá a vrací **Double**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**fmin –** , **fminf –** , **fminl**|C: \<Math. h ><br />C++: \<Math. h > nebo \<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[fmax, fmaxf, fmaxl](fmax-fmaxf-fmaxl.md)<br/>
