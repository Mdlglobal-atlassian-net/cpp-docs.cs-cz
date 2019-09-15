---
title: creal, crealf, creall
ms.date: 03/30/2018
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: ebd52a23765177d74f2bff5660f806ee5c4a9573
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942611"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Načte skutečnou část komplexního čísla.

## <a name="syntax"></a>Syntaxe

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní číslo.

## <a name="return-value"></a>Návratová hodnota

Skutečná část *z.*

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **creal** , která přijímají hodnoty **_Fcomplex** nebo **_Lcomplex** , a vracet hodnoty **float** nebo **Long Double** . V programu v jazyce C **creal** vždy převezme **_Dcomplex** hodnotu a vrátí hodnotu **Double** .

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**creal**, **crealf**, **creall**|\<complex.h>|\<ccomplex >|

Typy **_Fcomplex**, **_Dcomplex**a **_Lcomplex** jsou specifické pro společnost Microsoft ekvivalenty neimplementovaných nativních typů C99 typu **float _Complex**, **Double _Complex**a **Long Double _Complex**, v uvedeném pořadí. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>