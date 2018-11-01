---
title: _fpclass _fpclassf
ms.date: 04/05/2018
apiname:
- _fpclass
- _fpclassf
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
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: 987c87cc7a03f4a24e47654ae52e8a2416a15184
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590967"
---
# <a name="fpclass-fpclassf"></a>_fpclass _fpclassf

Vrátí hodnotu, která argumentu s plovoucí desetinnou čárkou klasifikace.

## <a name="syntax"></a>Syntaxe

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Hodnota s plovoucí desetinnou čárkou k testování.

## <a name="return-value"></a>Návratová hodnota

**_Fpclass** a **_fpclassf** funkce vrátí celočíselnou hodnotu, která určuje argumentu s plovoucí desetinnou čárkou klasifikaci *x*. Klasifikace může mít jeden z následujících hodnot podle \<float.h >.

|Hodnota|Popis|
|-----------|-----------------|
|**_FPCLASS_SNAN**|Signalizace NaN|
|**_FPCLASS_QNAN**|Tichý NaN|
|**_FPCLASS_NINF**|Záporné nekonečno (-INF)|
|**_FPCLASS_NN**|Negativní normalized nenulové|
|**_FPCLASS_ND**|Negativní denormalizovaný|
|**_FPCLASS_NZ**|Záporná nula (- 0)|
|**_FPCLASS_PZ**|Pozitivní 0 (+ 0)|
|**_FPCLASS_PD**|Pozitivní denormalizovaný|
|**_FPCLASS_PN**|Pozitivní normalized nenulové|
|**_FPCLASS_PINF**|Kladné nekonečno (+ INF)|

## <a name="remarks"></a>Poznámky

**_Fpclass** a **_fpclassf** funkce jsou specifické pro Microsoft. Když se podobají [fpclassify –](fpclassify.md), ale vrátí podrobnější informace o argument. **_Fpclassf** funkce dostupná jenom při kompilaci pro x64 platformy.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h >|

Kompatibilita a shoda podrobnosti, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>