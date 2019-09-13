---
title: cexp, cexpf, cexpl
ms.date: 11/04/2016
api_name:
- cexp
- cexpf
- cexpl
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
- cexp
- cexpf
- cexpl
- complex/cepx
- complex/cexpf
- complex/cexpl
helpviewer_keywords:
- cexp function
- cexpl function
- cexpf function
ms.assetid: f27fd5a9-70c7-4957-a7ee-5256d19bd1da
ms.openlocfilehash: 0dd6c9deddfe93cf044985f93b2129695d0770f0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943168"
---
# <a name="cexp-cexpf-cexpl"></a>cexp, cexpf, cexpl

Vypočítá exponenciální základ komplexního čísla od základu e.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex cexp( _Dcomplex z );
_Fcomplex cexpf( _Fcomplex z );
_Lcomplex cexpl( _Lcomplex z );
```

```cpp
_Fcomplex cexp( _Fcomplex z );  // C++ only
_Lcomplex cexp( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parametry

*z*<br/>
Komplexní číslo představující exponent.

## <a name="return-value"></a>Návratová hodnota

Hodnota **e** umocněná na mocninu *z*.

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **cexp** , která přijímají a vracejí hodnoty **_Fcomplex** a **_Lcomplex** . V programu v jazyce C **cexp** vždycky přebírá a vrací hodnotu **_Dcomplex** .

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**cexp**, **cexpf**, **cexpl**|\<complex.h>|\<complex.h>|

Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
[clog, clogf, clogl](clog-clogf-clogl.md)<br/>
