---
title: ___lc_locale_name_func
ms.date: 4/2/2020
api_name:
- ___lc_locale_name_func
- _o____lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: f38d4d9b11189a8313b26dd3313a5def800c2410
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351115"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Interní funkce CRT. Načte aktuální název národního prostředí vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec, který obsahuje aktuální název národního prostředí vlákna.

## <a name="remarks"></a>Poznámky

`___lc_locale_name_func`je interní funkce CRT, která je používána jinými funkcemi CRT k získání aktuálního názvu národního prostředí z místního úložiště vlákna pro data CRT. Tyto informace jsou také k dispozici pomocí [funkce _get_current_locale](../c-runtime-library/reference/get-current-locale.md) nebo [funkce setlocale _wsetlocale.](../c-runtime-library/reference/setlocale-wsetlocale.md)

Interní funkce CRT jsou specifické pro implementaci a mohou se měnit s každou verzí. Nedoporučujeme jejich použití ve vašem kódu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
