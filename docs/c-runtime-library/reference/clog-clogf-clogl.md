---
title: clog, clogf, clogl
ms.date: 11/04/2016
api_name:
- clog
- clogf
- clogl
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
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: 76ee6e4e81c275c8cbed0f74914521c0b44499bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942926"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Načte přirozený logaritmus komplexního čísla s vyjmutím větve kolem záporné reálné osy.

## <a name="syntax"></a>Syntaxe

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Základ logaritmu

## <a name="return-value"></a>Návratová hodnota

Přirozený logaritmus z *.* Výsledek není ohraničený podél reálné osy a v intervalu [-iπ, + iπ] podél imaginární osy.

Možné vrácené hodnoty jsou:

|parametr z|Návratová hodnota|
|-----------------|------------------|
|Kladné|Logaritmus o základu 10 z|
|Nula|- ∞|
|Záporný|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Poznámky

Vzhledem C++ k tomu, že umožňuje přetížení, můžete volat přetížení **CLOG** , která přijímají a vracejí hodnoty **_Fcomplex** a **_Lcomplex** . V programu v jazyce C **CLOG** vždycky přebírá a vrací hodnotu **_Dcomplex** .

## <a name="requirements"></a>Požadavky

|Rutina|Hlavička jazyka C|C++hlaviček|
|-------------|--------------|------------------|
|**CLOG**, **clogf**, **clogl**|\<complex.h>|\<ccomplex >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
