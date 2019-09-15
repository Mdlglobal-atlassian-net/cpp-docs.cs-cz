---
title: _get_current_locale
ms.date: 11/04/2016
api_name:
- _get_current_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a17e730b350eaf88cf1c51502fda3df5ae30f611
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956083"
---
# <a name="_get_current_locale"></a>_get_current_locale

Získá objekt národního prostředí představující aktuální národní prostředí.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Návratová hodnota

Objekt národního prostředí představující aktuální národní prostředí.

## <a name="remarks"></a>Poznámky

Funkce **_get_current_locale** získá aktuálně nastavené národní prostředí pro vlákno a vrátí objekt národního prostředí, který představuje toto národní prostředí.

Předchozí název této funkce, **__get_current_locale** (se dvěma počátečními podtržítky), byl zastaralý.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_current_locale**|\<locale. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
