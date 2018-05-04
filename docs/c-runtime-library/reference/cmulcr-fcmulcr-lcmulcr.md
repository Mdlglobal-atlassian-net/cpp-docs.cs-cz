---
title: _Cmulcr, _FCmulcr, _LCmulcr | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cmulcr
- _FCmulcr
- _LCmulcr
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
- _Cmulcr
- _FCmulcr
- _LCmulcr
- complex/_Cmulcr
- complex/_FCmulcr
- complex/_LCmulcr
dev_langs:
- C++
helpviewer_keywords:
- _Cmulcr function
- _FCmulcr function
- _LCmulcr function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbd42e4c543d4bc42afa023d62b328a143c90374
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="cmulcr-fcmulcr-lcmulcr"></a>_Cmulcr, _FCmulcr, _LCmulcr

Vynásobí komplexní číslo, číslo s plovoucí desetinnou čárkou.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cmulcr( _Dcomplex x, double y );
_Fcomplex _FCmulcr( _Fcomplex x, float y );
_Lcomplex _LCmulcr( _Lcomplex x, long double y );
```

### <a name="parameters"></a>Parametry

*x*<br/>
Jeden z komplexní operandy mají vynásobit.

*y*<br/>
S plovoucí desetinnou čárkou operand mají vynásobit.

## <a name="return-value"></a>Návratová hodnota

A **_Dcomplex**, **_Fcomplex**, nebo **_Lcomplex** struktura, která představuje komplexní Součin komplexního čísla *x* a číslo flaoting bodu *y*.

## <a name="remarks"></a>Poznámky

Protože integrované aritmetické operátory nefungují na implementaci Microsoft komplexních typů **_Cmulcr**, **_FCmulcr**, a **_LCmulcr** funkce zjednodušení násobení komplexní typy s plovoucí desetinnou čárkou typy.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**_Cmulcr**, **_FCmulcr**, **_LCmulcr**|\<complex.h>|\<complex.h>|

Tyto funkce jsou specifické pro společnost Microsoft. Typy **_Dcomplex**, **_Fcomplex**, a **_Lcomplex** jsou specifické pro společnost Microsoft – ekvivalenty k neimplementované nativní typy C99 **dvojité _complex –** , **float _complex –**, a **_complex long double –**, v uvedeném pořadí. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[Norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
