---
title: log2 – log2f –, log2l
ms.date: 04/05/2018
apiname:
- log2
- log2l
- log2f
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
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 5f1db48abdc7237dc46a0ea8a3ea5647a0fce62f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579306"
---
# <a name="log2-log2f-log2l"></a>log2 – log2f –, log2l

Určuje binární logaritmus (základ-2) zadanou hodnotu.

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
Hodnota určená k určení logaritmus o základu 2 z.

## <a name="return-value"></a>Návratová hodnota

V případě úspěchu vrátí vrátit log2 *x*.

V opačném případě může vracet instanci jednoho z následujících hodnot:

|Problém|Vrátí|
|-----------|------------|
|*x* < 0|NaN|
|*x* = ±0|-NEKONEČNO|
|*x* = 1|+0|
|+ NEKONEČNO|+ NEKONEČNO|
|NaN|NaN|
|chyby domény|NaN|
|Chyba pole|– HUGE_VAL, - HUGE_VALF, nebo - HUGE_VALL|

Jsou hlášeny chyby uvedené v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Pokud x je celé číslo, vrátí funkce v podstatě index založený na nule nejvýznamnější 1 bit *x*.

## <a name="requirements"></a>Požadavky

|Funkce|Záhlaví C|Hlaviček jazyka C++|
|--------------|--------------|------------------|
|**log2 –**, **log2f –**, **log2l**|\<Math.h >|\<cmath >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
