---
title: log2, log2f, log2l
ms.date: 4/2/2020
api_name:
- log2
- log2l
- log2f
- _o_log2
- _o_log2f
- _o_log2l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
ms.openlocfilehash: 58da7790e6fbce915c16a02a1b0d972a6fe1049e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911416"
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

*znak*<br/>
Hodnota, která určuje logaritmus o základu 2.

## <a name="return-value"></a>Návratová hodnota

Po úspěšném návratu vrátí log2 – *x*.

V opačném případě může vracet jednu z následujících hodnot:

|Problém|Vrátit|
|-----------|------------|
|*x* < 0|Není číslo|
|*x* = ± 0|– Nekonečno|
|*x* = 1|+ 0|
|+ Nekonečno|+ Nekonečno|
|Není číslo|Není číslo|
|Chyba domény|Není číslo|
|Chyba pole|-HUGE_VAL,-HUGE_VALF nebo-HUGE_VALL|

Chyby jsou hlášeny tak, jak jsou uvedeny v [_matherr](matherr.md).

## <a name="remarks"></a>Poznámky

Pokud x je celé číslo, tato funkce v podstatě vrátí index s nejvýraznějším 1 bitem hodnoty *x*od nuly.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Hlavička jazyka C|Hlavička C++|
|--------------|--------------|------------------|
|**log2 –**, **log2f –**, **log2l**|\<Math. h>|\<cmath>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](crt-alphabetical-function-reference.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
