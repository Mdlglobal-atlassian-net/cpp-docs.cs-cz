---
title: _ismbbalpha, _ismbbalpha_l
ms.date: 4/2/2020
api_name:
- _ismbbalpha
- _ismbbalpha_l
- _o__ismbbalpha
- _o__ismbbalpha_l
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
ms.openlocfilehash: 1fa92d8e0f0ed331110666add1015fbdacf20f07
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917501"
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

*r*<br/>
Celé číslo, které se má testovat.

*locale*<br/>
Národní prostředí, které se má použít.

## <a name="return-value"></a>Návratová hodnota

**_ismbbalpha** vrací nenulovou hodnotu, pokud výraz:

`isalpha(c) || _ismbbkalnum(c)`

je nenulové pro *c*nebo 0, pokud není. **_ismbbalpha** používá aktuální národní prostředí pro všechna nastavení znaků závislá na národním prostředí. **_ismbbalpha_l** je totožný s tím rozdílem, že používá předané národní prostředí.

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_ismbbalpha**|\<Mbctype. h>|
|**_ismbbalpha_l**|\<Mbctype. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[Klasifikace bajtů](../../c-runtime-library/byte-classification.md)<br/>
[Rutiny _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
