---
title: ___lc_collate_cp_func
ms.date: 4/2/2020
api_name:
- ___lc_collate_cp_func
- _o____lc_collate_cp_func
api_location:
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_collate_cp_func
helpviewer_keywords:
- ___lc_collate_cp_func
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
ms.openlocfilehash: 241292f22beea0cbf4e14d1b4480f6621ef6ccca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351136"
---
# <a name="___lc_collate_cp_func"></a>___lc_collate_cp_func

Interní funkce CRT. Načte aktuální znakovou stránku kolace vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Aktuální znaková stránka kolace vlákna.

## <a name="remarks"></a>Poznámky

`___lc_collate_cp_func`je interní funkce CRT, která je používána jinými funkcemi CRT k získání aktuální znakové stránky řazení z místního úložiště vlákna pro data CRT. Tyto informace jsou také k dispozici pomocí [funkce _get_current_locale.](../c-runtime-library/reference/get-current-locale.md)

Interní funkce CRT jsou specifické pro implementaci a mohou se měnit s každou verzí. Nedoporučujeme jejich použití ve vašem kódu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___lc_collate_cp_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Viz také

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
