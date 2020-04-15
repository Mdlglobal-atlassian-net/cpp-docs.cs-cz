---
title: ___lc_codepage_func
ms.date: 4/2/2020
api_name:
- ___lc_codepage_func
- _o____lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: 2f3eeb4611a0a41ff1782e0b162cd65d86d3ef65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351238"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

Interní funkce CRT. Načte aktuální znakovou stránku vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Aktuální znaková stránka vlákna.

## <a name="remarks"></a>Poznámky

`___lc_codepage_func`je interní funkce CRT, která je používána jinými funkcemi CRT k získání aktuální znakové stránky z místního úložiště vlákna pro data CRT. Tyto informace jsou také k dispozici pomocí [funkce _get_current_locale.](../c-runtime-library/reference/get-current-locale.md)

*Znaková stránka* je mapování jednobajtových nebo dvoubajtových kódů na jednotlivé znaky. Různé znakové stránky obsahují různé speciální znaky, které jsou obvykle přizpůsobeny pro jazyk nebo skupinu jazyků. Další informace o znakových stránkách naleznete v [tématu Code Pages](../c-runtime-library/code-pages.md).

Interní funkce CRT jsou specifické pro implementaci a mohou se měnit s každou verzí. Nedoporučujeme jejich použití ve vašem kódu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
