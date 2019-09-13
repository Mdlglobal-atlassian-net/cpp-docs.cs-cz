---
title: _ismbbpunct, _ismbbpunct_l
ms.date: 11/04/2016
api_name:
- _ismbbpunct
- _ismbbpunct_l
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
- ismbbpunct
- ismbbpunct_l
- _ismbbpunct_l
- _ismbbpunct
helpviewer_keywords:
- ismbbpunct function
- _ismbbpunct function
- ismbbpunct_l function
- _ismbbpunct_l function
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
ms.openlocfilehash: 8a56df7ffda64a2a2cecaac6bc15d2cbaa1d0a71
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953986"
---
# <a name="_ismbbpunct-_ismbbpunct_l"></a>_ismbbpunct, _ismbbpunct_l

Určuje, zda je konkrétní znak interpunkční znak.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbpunct(
   unsigned int c
);
int _ismbbpunct_l(
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

**_ismbbpunct** vrací nenulovou hodnotu, pokud celé číslo *c* je symbol interpunkce mimo ASCII. **_ismbbpunct** používá aktuální národní prostředí pro všechna nastavení znaků závislá na národním prostředí. **_ismbbpunct_l** je totožný s tím rozdílem, že používá národní prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbpunct**|\<Mbctype. h >|
|**_ismbbpunct_l**|\<Mbctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
