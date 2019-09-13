---
title: _ismbbalnum, _ismbbalnum_l
ms.date: 11/04/2016
api_name:
- _ismbbalnum
- _ismbbalnum_l
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
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
ms.openlocfilehash: d817ea6875149f9342854b0c22b27b0c93d29636
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954301"
---
# <a name="_ismbbalnum-_ismbbalnum_l"></a>_ismbbalnum, _ismbbalnum_l

Určuje, zda je zadaný vícebajtový znak alfa nebo numerický.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbalnum(
   unsigned int c
);
int _ismbbalnum_l(
   unsigned int c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo, které se má testovat.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbalnum** vrací nenulovou hodnotu, pokud výraz:

`isalnum(c) || _ismbbkalnum(c)`

je nenulové pro *c*nebo 0, pokud není.

Verze této funkce s příponou **_l** je shodná s tím rozdílem, že používá předané národní prostředí namísto aktuálního národního prostředí pro své chování závislé na národním prostředí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbalnum**|\<Mbctype. h >|
|**_ismbbalnum_l**|\<Mbctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
