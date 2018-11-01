---
title: _Cbuild _FCbuild, _LCbuild
ms.date: 03/30/2018
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
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: 5565c87a3cccd1715a1357f417238587f3fba4d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511797"
---
# <a name="cbuild-fcbuild-lcbuild"></a>_Cbuild _FCbuild, _LCbuild

Sestaví komplexního čísla z reálné a imaginární části.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>Parametry

*Real*<br/>
Skutečné součástí komplexní čísla k vytvoření.

*pomyslná*<br/>
Imaginární části komplexního čísla k vytvoření.

## <a name="return-value"></a>Návratová hodnota

A **_Dcomplex**, **_Fcomplex**, nebo **_Lcomplex** struktura, která představuje komplexní čísla (*skutečné*, *imaginární*  \* můžu) pro hodnoty s plovoucí desetinnou čárkou typu zadaný.

## <a name="remarks"></a>Poznámky

**_Cbuild**, **_FCbuild**, a **_LCbuild** funkce zjednodušení vytváření komplexních typů. Použití [creal crealf, creall](creal-crealf-creall.md) a [cimag cimagf, cimagl](cimag-cimagf-cimagl.md) funkce k načtení reálné a imaginární části zastoupené komplexní čísla.

## <a name="requirements"></a>Požadavky

|Rutina|Záhlaví C|Hlaviček jazyka C++|
|-------------|--------------|------------------|
|**_Cbuild**, **_FCbuild**, **_LCbuild**|\<complex.h>|\<ccomplex >|

Tyto funkce jsou specifické pro společnost Microsoft. Typy **_Dcomplex**, **_Fcomplex**, a **_Lcomplex** jsou specifické pro společnost Microsoft – ekvivalenty k neimplementovaná C99 nativní typy **double _Complex** , **float _Complex**, a **long double _Complex**v uvedeném pořadí. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc, _FCmulcc, _LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr, _FCmulcr, _LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[Norm a normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
