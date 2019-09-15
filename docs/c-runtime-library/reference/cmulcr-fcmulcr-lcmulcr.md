---
title: _Cmulcr, _FCmulcr, _LCmulcr
ms.date: 03/30/2018
api_name:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
ms.openlocfilehash: cbff1c2cb0e66da77b6fdc8127b78fb475aa5080
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942888"
---
# <a name="_cmulcr-_fcmulcr-_lcmulcr"></a>_Cmulcr, _FCmulcr, _LCmulcr

Vynásobí komplexní číslo číslem s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>Parametry

*x*<br/>
Jeden ze složitých operandů k násobení.

*y*<br/>
Operand s plovoucí desetinnou čárkou, který se má vynásobit.

## <a name="return-value"></a>Návratová hodnota

Struktura **_Dcomplex**, **_Fcomplex**nebo **_Lcomplex** , která představuje komplexní produkt se složitým číslem *x* a Flaoting-Point číslo *y*.

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že předdefinované aritmetické operátory nefungují na implementaci komplexních typů od společnosti Microsoft, funkce **_Cmulcr**, **_FCmulcr**a **_LCmulcr** zjednodušují násobení složitých typů pomocí typů s plovoucí desetinnou čárkou.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**_Cmulcr**, **_FCmulcr**, **_LCmulcr**|\<complex.h>|\<complex.h>|

Tyto funkce jsou specifické pro společnost Microsoft. Typy **_Dcomplex**, **_Fcomplex**a **_Lcomplex** jsou ekvivalenty od společnosti Microsoft pro neimplementované nativní typy C99 **Double _Complex**, **float _Complex**a **Long Double _Complex**, v uvedeném pořadí. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
