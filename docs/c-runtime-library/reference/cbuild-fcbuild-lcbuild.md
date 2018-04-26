---
title: _Cbuild, _FCbuild, _LCbuild | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _Cbuild
- _FCbuild
- _LCbuild
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
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
dev_langs:
- C++
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 555cd1d9d8f22801b1d3f3341be9041b1dde548c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild, _FCbuild, _LCbuild

Vytvoří číslo komplexní od skutečné a pomyslná částí.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Parametry

*skutečné*<br/>
Skutečné část reprezentující komplexní čísla vytvořit.

*pomyslná*<br/>
Pomyslná část reprezentující komplexní čísla vytvořit.

## <a name="return-value"></a>Návratová hodnota

A **_Dcomplex**, **_Fcomplex**, nebo **_Lcomplex** struktura, která představuje reprezentující komplexní čísla (*skutečné*, *pomyslná*  \* i) pro hodnoty s plovoucí desetinnou čárkou zadaného typu.

## <a name="remarks"></a>Poznámky

**_Cbuild**, **_FCbuild**, a **_LCbuild** funkce zjednodušuje vytváření komplexních typů. Použití [creal, crealf, creall](creal-crealf-creall.md) a [cimag, cimagf, cimagl](cimag-cimagf-cimagl.md) funkce načíst části skutečné a pomyslná reprezentována komplexní čísla.

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička C|Hlavička C++|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild**, **_LCbuild**|\<complex.h>|\<ccomplex >|

Tyto funkce jsou specifické pro společnost Microsoft. Typy **_Dcomplex**, **_Fcomplex**, a **_Lcomplex** jsou specifické pro společnost Microsoft – ekvivalenty k neimplementované nativní typy C99 **dvojité _complex –** , **float _complex –**, a **_complex long double –**, v uvedeném pořadí. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[Norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
