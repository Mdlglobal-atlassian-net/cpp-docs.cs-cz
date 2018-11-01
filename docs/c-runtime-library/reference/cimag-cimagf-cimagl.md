---
title: cimag cimagf, cimagl
ms.date: 11/04/2016
apiname:
- cimag
- cimagf
- cimagl
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
- cimagf
- cimagl
- complex/cimag
- complex/cimagf
- complex/cimagl
- cimag
helpviewer_keywords:
- cimag function
- cimagf function
- cimagl function
ms.assetid: 0d8836f5-d61d-44cd-8731-6f75cb776def
ms.openlocfilehash: 6f5067967aa62894abb5316f60074b5125b1cba1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572728"
---
# <a name="cimag-cimagf-cimagl"></a>cimag cimagf, cimagl

Načte imaginární části komplexního čísla.

## <a name="syntax"></a>Syntaxe

```C
double cimag( _Dcomplex z );
float cimagf( _Fcomplex z );
long double cimagl( _Lcomplex z );
```

```cpp
float cimag( _Fcomplex z );  // C++
long double cimag( _Lcomplex z );  // C++
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní čísla.

## <a name="return-value"></a>Návratová hodnota

Imaginární části *z*.

## <a name="remarks"></a>Poznámky

Protože jazyk C++ umožňuje přetížení, můžete volat přetížení **cimag** trvají **_Fcomplex** nebo **_Lcomplex** hodnoty a návrat **float** nebo **dlouhé** **double** hodnoty. V programu jazyka C **cimag** vždy přijímá **_Dcomplex** hodnotu a vrátí **double** hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Záhlaví C|Hlaviček jazyka C++|
|-------------|--------------|------------------|
|**cimag**, **cimagf**, **cimagl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[Norm a normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
