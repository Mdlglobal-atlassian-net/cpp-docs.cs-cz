---
title: _ismbbkpunct, _ismbbkpunct_l
ms.date: 11/04/2016
api_name:
- _ismbbkpunct_l
- _ismbbkpunct
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbbkpunct_l
- _ismbbkpunct_l
- ismbbkpunct
- _ismbbkpunct
helpviewer_keywords:
- _ismbbkpunct_l function
- ismbbkpunct_l function
- ismbbkpunct function
- _ismbbkpunct function
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
ms.openlocfilehash: 35f09013fbbe522a1eb747f2d2131a5fbb23f765
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954091"
---
# <a name="_ismbbkpunct-_ismbbkpunct_l"></a>_ismbbkpunct, _ismbbkpunct_l

Kontroluje, zda vícebajtový znak je znak interpunkce.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbkpunct(
   unsigned int c
);
int _ismbbkpunct_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo, které se má testovat.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbkpunct** vrací nenulovou hodnotu, pokud celé číslo *c* je symbol interpunkce mimo ASCII, nebo 0, pokud není. Například pouze v kódové stránce 932 **_ismbbkpunct** testy pro interpunkční znaménka Katakana. **_ismbbkpunct** používá aktuální národní prostředí pro všechna nastavení znaků závislá na národním prostředí. **_ismbbkpunct_l** je totožný s tím rozdílem, že používá národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbkpunct**|\<Mbctype. h >|
|**_ismbbkpunct_l**|\<Mbctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
