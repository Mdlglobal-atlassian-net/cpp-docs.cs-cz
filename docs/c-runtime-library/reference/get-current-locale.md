---
title: _get_current_locale
ms.date: 11/04/2016
apiname:
- _get_current_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_current_locale
- __get_current_locale
- _get_current_locale
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
ms.openlocfilehash: 87c30ee701d8f7d3a89a0aa61ba18a7f854bc9b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511888"
---
# <a name="getcurrentlocale"></a>_get_current_locale

Získá místní objekt představující aktuální národní prostředí.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Návratová hodnota

Místní objekt představující aktuální národní prostředí.

## <a name="remarks"></a>Poznámky

**_Get_current_locale –** funkce získá v současné době nastavené národního prostředí pro vlákno a vrátí objekt národního prostředí představující toto národní prostředí.

Předchozí název této funkce **__get_current_locale –** (se dvěma vedoucími podtržítky) je zastaralá.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_current_locale**|\<Locale.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
