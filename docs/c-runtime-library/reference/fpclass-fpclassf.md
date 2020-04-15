---
title: _fpclass, _fpclassf
ms.date: 4/2/2020
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b16655fed046114e9dd8592c5e1fd3fc5f7ed4bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346280"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

Vrátí hodnotu označující klasifikaci argumentu s plovoucí desetinnou desetinnou desetinnou desetinnou.

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

*X*<br/>
Hodnota s plovoucí desetinnou tácem k testování.

## <a name="return-value"></a>Návratová hodnota

Funkce **_fpclass** a **_fpclassf** vrátí celočíselnou hodnotu, která označuje klasifikaci argumentu x s plovoucí desetinnou desetinnou desetinnou *desetinnou*hodnotou . Klasifikace může mít jednu z následujících hodnot definovaných v \<> float.h.

|Hodnota|Popis|
|-----------|-----------------|
|**_FPCLASS_SNAN**|Signalizace NaN|
|**_FPCLASS_QNAN**|Tichý NaN|
|**_FPCLASS_NINF**|Záporné nekonečno ( -INF)|
|**_FPCLASS_NN**|Záporná normalizovaná nenulová|
|**_FPCLASS_ND**|Negativní denormalizované|
|**_FPCLASS_NZ**|Záporná nula ( - 0)|
|**_FPCLASS_PZ**|Kladné 0 (+0)|
|**_FPCLASS_PD**|Pozitivní denormalizované|
|**_FPCLASS_PN**|Kladné normalizované nenulové|
|**_FPCLASS_PINF**|Kladné nekonečno (+INF)|

## <a name="remarks"></a>Poznámky

Funkce **_fpclass** a **_fpclassf** jsou specifické pro společnost Microsoft. Jsou podobné [fpclassify](fpclassify.md), ale vrátit podrobnější informace o argumentu. Funkce **_fpclassf** je k dispozici pouze při kompilaci pro platformu x64.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fpclass** **, _fpclassf**|\<float.h>|

Další informace o kompatibilitě a shodě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora s plovoucí desetinnou tálicí](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
