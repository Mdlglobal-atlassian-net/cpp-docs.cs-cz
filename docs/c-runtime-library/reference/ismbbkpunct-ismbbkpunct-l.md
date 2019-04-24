---
title: _ismbbkpunct, _ismbbkpunct_l
ms.date: 11/04/2016
apiname:
- _ismbbkpunct_l
- _ismbbkpunct
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 24a82bdf0dde2beb0978226208c151689e06ed72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287027"
---
# <a name="ismbbkpunct-ismbbkpunctl"></a>_ismbbkpunct, _ismbbkpunct_l

Kontroluje, zda je vícebajtový znak je znak interpunkce.

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
Celé číslo k testování.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_ismbbkpunct –** vrací nenulovou hodnotu, pokud celé číslo *c* je jiné než ASCII interpunkční symbol, nebo 0, pokud není. Například pouze v kódové stránce 932 **_ismbbkpunct –** interpunkční znaménka katakana. **_ismbbkpunct –** používá aktuální národní prostředí pro všechna nastavení závislé na národním prostředí znak. **_ismbbkpunct_l –** je totožný s tím rozdílem, že používá národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbkpunct**|\<mbctype.h>|
|**_ismbbkpunct_l**|\<mbctype.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
