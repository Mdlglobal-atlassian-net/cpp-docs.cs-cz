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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8287e2e7cab8880d35fef170287713adcc103c7e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912962"
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

Toto je interní funkce, kterou CRT používá k načtení aktuální hodnoty [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) makra z úložiště Thread Local. Doporučujeme použít `MB_CUR_MAX` makro v kódu pro přenositelnost.

`__mb_cur_max` Makro je pohodlný způsob, jak zavolat `___mb_cur_max_func()` funkci. `__p___mb_cur_max` Funkce je definována pro kompatibilitu s Visual C++ 5,0 a staršími verzemi.

Interní funkce CRT jsou specifické pro konkrétní implementaci a můžou se měnit s každou vydanou verzí. Nedoporučujeme jejich použití ve vašem kódu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<CType. h>, \<Stdlib. h>|

## <a name="see-also"></a>Viz také

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
