---
title: norm, normf, norml
ms.date: 04/05/2018
api_name:
- norm
- normf
- norml
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
- norm
- normf
- norml
- complex/norm
- complex/normf
- complex/norml
helpviewer_keywords:
- norm function
- normf function
- norml function
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
ms.openlocfilehash: 8deaa07d984a3840c73e594535ffffc9078d4716
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951321"
---
# <a name="norm-normf-norml"></a>norm, normf, norml

Načte čtvercovou velikost složeného čísla.

## <a name="syntax"></a>Syntaxe

```C
double norm( _Dcomplex z );
float normf( _Fcomplex z );
long double norml( _Lcomplex z );
```

```cpp
float norm( _Fcomplex z );  // C++ only
long double norm( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní číslo.

## <a name="return-value"></a>Návratová hodnota

Čtvercový *Rozsah z.*

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **normy** , které přijímají hodnoty **_Fcomplex** nebo **_Lcomplex** , a vracet hodnoty **float** nebo **Long Double** . V programu v jazyce C **norma** vždy přebírá hodnotu **_Dcomplex** a vrací hodnotu **Double** .

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**norma**, **normf**, **norma**|\<complex.h>|\<complex.h>|

Typy **_Fcomplex**, **_Dcomplex**a **_Lcomplex** jsou specifické pro společnost Microsoft ekvivalenty neimplementovaných nativních typů C99 typu **float _Complex**, **Double _Complex**a **Long Double _Complex**, v uvedeném pořadí.  Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
