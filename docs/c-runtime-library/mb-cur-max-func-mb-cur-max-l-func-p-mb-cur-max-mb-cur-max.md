---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 4/2/2020
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
- _o____mb_cur_max_func
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
ms.openlocfilehash: f9b9e2d903bb05f5b1b653b4fb51c57b354d4126
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351080"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Interní funkce CRT. Načte maximální počet bajtů v vícebajtovém znaku pro aktuální nebo zadané národní prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parametry

národní prostředí: Struktura národního prostředí, ze které má být výsledek načten. Pokud je tato hodnota null, použije se aktuální národní prostředí vlákna.

## <a name="return-value"></a>Návratová hodnota

Maximální počet bajtů v vícebajtovém znaku pro aktuální národní prostředí vlákna nebo zadané národní prostředí.

## <a name="remarks"></a>Poznámky

Toto je interní funkce, kterou crt používá k načtení aktuální hodnoty [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) makro z místního úložiště vlákna. Doporučujeme použít `MB_CUR_MAX` makro v kódu pro přenositelnost.

Makro `__mb_cur_max` je pohodlný způsob, `___mb_cur_max_func()` jak volat funkci. Funkce `__p___mb_cur_max` je definována pro kompatibilitu s Visual C++ 5.0 a staršími verzemi.

Interní funkce CRT jsou specifické pro implementaci a mohou se měnit s každou verzí. Nedoporučujeme jejich použití ve vašem kódu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Viz také

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
