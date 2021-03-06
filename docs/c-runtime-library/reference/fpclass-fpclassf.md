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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a6591d9348739d27831785a05f4a602aacdd4d0c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914851"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

Vrací hodnotu určující klasifikaci argumentu s plovoucí desetinnou čárkou.

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

*znak*<br/>
Hodnota s plovoucí desetinnou čárkou, která má být testována.

## <a name="return-value"></a>Návratová hodnota

Funkce **_fpclass** a **_fpclassf** vrací celočíselnou hodnotu, která označuje klasifikaci plovoucí desetinné čárky argumentu *x*. Klasifikace může mít jednu z následujících hodnot, která je definována v \<float. h>.

|Hodnota|Popis|
|-----------|-----------------|
|**_FPCLASS_SNAN**|Signalizace – NaN|
|**_FPCLASS_QNAN**|Tiché NaN|
|**_FPCLASS_NINF**|Záporné nekonečno (-INF)|
|**_FPCLASS_NN**|Záporná normalizovaná nenulová hodnota|
|**_FPCLASS_ND**|Záporné denormalizované|
|**_FPCLASS_NZ**|Záporné nula (-0)|
|**_FPCLASS_PZ**|Kladné 0 (+ 0)|
|**_FPCLASS_PD**|Kladné denormalizované|
|**_FPCLASS_PN**|Kladná normalizovaná hodnota nenulového typu|
|**_FPCLASS_PINF**|Kladné nekonečno (+ INF)|

## <a name="remarks"></a>Poznámky

Funkce **_fpclass** a **_fpclassf** jsou specifické pro společnost Microsoft. Jsou podobné jako [fpclassify –](fpclassify.md), ale vracejí podrobnější informace o argumentu. Funkce **_fpclassf** je k dispozici pouze v případě, že je zkompilována pro platformu x64.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fpclass** **_fpclassf**|\<float. h>|

Další informace o kompatibilitě a dodržování shody najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>
