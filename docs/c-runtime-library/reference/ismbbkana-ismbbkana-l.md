---
title: _ismbbkana, _ismbbkana_l
ms.date: 4/2/2020
api_name:
- _ismbbkana_l
- _ismbbkana
- _o__ismbbkana
- _o__ismbbkana_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbbkana_l
- ismbbkana_l
- ismbbkana
- _ismbbkana
helpviewer_keywords:
- _ismbbkana_l function
- _ismbbkana function
- ismbbkana function
- ismbbkana_l function
ms.assetid: 64d4eb4a-205a-40ef-be35-ff9d77fabbaf
ms.openlocfilehash: dd788d18692e11886caf4ee12703bb5878de1163
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918935"
---
# <a name="_ismbbkana-_ismbbkana_l"></a>_ismbbkana, _ismbbkana_l

Testuje symbol Katakana a je specifický pro znakovou stránku 932.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbkana(
   unsigned int c
);
int _ismbbkana_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
Celé číslo, které se má testovat.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbkana** vrátí nenulovou hodnotu, pokud je celé číslo *c* symbol Katakana nebo 0, pokud není. **_ismbbkana** používá aktuální národní prostředí pro informace o znacích závislé na národním prostředí. **_ismbbkana_l** je totožný s tím rozdílem, že používá předaný objekt národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbkana**|\<Mbctype. h>|
|**_ismbbkana_l**|\<Mbctype. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
