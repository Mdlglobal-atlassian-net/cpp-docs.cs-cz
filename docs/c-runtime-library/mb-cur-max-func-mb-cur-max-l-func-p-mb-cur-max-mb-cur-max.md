---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 11/04/2016
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
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
ms.openlocfilehash: a37ae2134d92310d6a530c759559b5e4b4af00f6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944200"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Vnitřní funkce CRT. Načte maximální počet bajtů v vícebajtovém znaku pro aktuální nebo zadané národní prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parametry

národní prostředí, ze kterého struktura národního prostředí Získá výsledek. Pokud je tato hodnota null, použije se aktuální národní prostředí vlákna.

## <a name="return-value"></a>Návratová hodnota

Maximální počet bajtů v vícebajtovém znaku pro aktuální národní prostředí vlákna nebo zadané národní prostředí.

## <a name="remarks"></a>Poznámky

Toto je interní funkce, kterou CRT používá k načtení aktuální hodnoty makra [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) z Thread localho úložiště. Doporučujeme použít `MB_CUR_MAX` makro v kódu pro přenositelnost.

Makro je pohodlný způsob, jak `___mb_cur_max_func()` zavolat funkci. `__mb_cur_max` Funkce je definována pro kompatibilitu s Visual C++ 5,0 a staršími verzemi. `__p___mb_cur_max`

Interní funkce CRT jsou specifické pro konkrétní implementaci a můžou se měnit s každou vydanou verzí. Nedoporučujeme jejich použití ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<CType. h >, \<Stdlib. h >|

## <a name="see-also"></a>Viz také:

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
