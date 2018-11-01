---
title: _ismbbkalnum, _ismbbkalnum_l
ms.date: 11/04/2016
apiname:
- _ismbbkalnum
- _ismbbkalnum_l
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
- _ismbbkalnum
- ismbbkalnum
- ismbbkalnum_l
- _ismbbkalnum_l
helpviewer_keywords:
- _ismbbkalnum_l function
- ismbbkalnum_l function
- _ismbbkalnum function
- ismbbkalnum function
ms.assetid: e1d70e7b-29d0-469c-9d93-442b99de22ac
ms.openlocfilehash: 4eca5738068dab7393f70edf619629b179637e73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481052"
---
# <a name="ismbbkalnum-ismbbkalnuml"></a>_ismbbkalnum, _ismbbkalnum_l

Určuje, zda je určitý vícebajtový znak ne ASCII textový symbol.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbkalnum(
   unsigned int c
);
int _ismbbkalnum_l(
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

**_ismbbkalnum –** vrací nenulovou hodnotu, pokud celé číslo *c* je ne ASCII textový symbol jiný než interpunkce, nebo 0, pokud není. **_ismbbkalnum –** používá aktuální národní prostředí pro závislé na národním prostředí znak informace. **_ismbbkalnum_l –** je stejný jako **_ismbbkalnum –** s tím rozdílem, že přijímá jako parametr národního prostředí. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbkalnum**|\<Mbctype.h >|
|**_ismbbkalnum_l**|\<Mbctype.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
