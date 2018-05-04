---
title: _get_current_locale – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- get_current_locale function
- _get_current_locale function
- locales, getting information on
- __get_current_locale function
ms.assetid: 572217f2-a37a-4105-a293-a250b4fabd99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c658d960953bea2890202bebe280d46dd3407d63
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="getcurrentlocale"></a>_get_current_locale

Získá objekt národního prostředí představující aktuální národní prostředí.

## <a name="syntax"></a>Syntaxe

```C
_locale_t _get_current_locale(void);
```

## <a name="return-value"></a>Návratová hodnota

Objekt národního prostředí představující aktuální národní prostředí.

## <a name="remarks"></a>Poznámky

**_Get_current_locale –** funkce získá aktuálně nastavené národní prostředí pro vlákno a vrátí objekt národního prostředí reprezentující toto národní prostředí.

Předchozí název této funkce **__get_current_locale –** (se dvěma úvodní podtržítka) je zastaralá.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_current_locale**|\<Locale.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
