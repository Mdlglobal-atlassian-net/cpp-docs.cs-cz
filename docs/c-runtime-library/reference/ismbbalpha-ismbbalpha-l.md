---
title: _ismbbalpha, _ismbbalpha_l
ms.date: 11/04/2016
api_name:
- _ismbbalpha
- _ismbbalpha_l
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
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
ms.openlocfilehash: fe60eec2eb7f93d866340aabe382bf32d6b04b21
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954260"
---
# <a name="_ismbbalpha-_ismbbalpha_l"></a>_ismbbalpha, _ismbbalpha_l

Určuje, zda je zadaný vícebajtový znak alfa.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbalpha(
   unsigned int c
);
int _ismbbalpha_l(
   unsigned int c
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Celé číslo, které se má testovat.

*jazyka*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbalpha** vrací nenulovou hodnotu, pokud výraz:

`isalpha(c) || _ismbbkalnum(c)`

je nenulové pro *c*nebo 0, pokud není. **_ismbbalpha** používá aktuální národní prostředí pro všechna nastavení znaků závislá na národním prostředí. **_ismbbalpha_l** je totožný s tím rozdílem, že používá předané národní prostředí.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbalpha**|\<Mbctype. h >|
|**_ismbbalpha_l**|\<Mbctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)<br/>
