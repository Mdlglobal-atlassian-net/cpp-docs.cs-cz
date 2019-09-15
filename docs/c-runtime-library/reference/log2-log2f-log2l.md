---
title: log2, log2f, log2l
ms.date: 04/05/2018
api_name:
- log2
- log2l
- log2f
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: bf1734ea2f96fa1c09b3b0d1f43b681fc31c8f9f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953158"
---
# <a name="log2-log2f-log2l"></a>log2, log2f, log2l

Určuje dvojkový logaritmus (dekadický-2) zadané hodnoty.

## <a name="syntax"></a>Syntaxe

```C
double log2(
   double x
);

float log2(
   float x
); //C++ only

long double log2(
   long double x
); //C++ only

float log2f(
   float x
);

long double log2l(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota, která určuje logaritmus o základu 2.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném návratu vrátí log2 – *x*.

V opačném případě může vracet jednu z následujících hodnot:

|Problém|vrátit|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|– NEKONEČNO|
|*x* = 1|+0|
|\+ NEKONEČNO|\+ NEKONEČNO|
|NaN|NaN|
|Chyba domény|NaN|
|Chyba pole|-HUGE_VAL,-HUGE_VALF nebo-HUGE_VALL|

Chyby jsou hlášeny podle zadání v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Pokud x je celé číslo, tato funkce v podstatě vrátí index s nejvýraznějším 1 bitem hodnoty *x*od nuly.

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|C++hlaviček|
|--------------|--------------|------------------|
|**log2 –** , **log2f –** , **log2l**|\<Math. h >|\<cmath >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
