---
title: ___mb_cur_max_func ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 11/04/2016
apiname:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
apilocation:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 9d5178a9a0801767019b713696ddf809c3fe6f0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342762"
---
# <a name="mbcurmaxfunc-mbcurmaxlfunc-pmbcurmax-mbcurmax"></a>___mb_cur_max_func ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Vnitřní funkce CRT. Získá maximální počet bajtů ve vícebajtové znakové pro aktuálního nebo zadaného národního prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parametry

Struktura národní prostředí načíst výsledky z národního prostředí. Pokud je tato hodnota null, použije se aktuální národní prostředí pro vlákno.

## <a name="return-value"></a>Návratová hodnota

Maximální počet bajtů ve vícebajtové znakové pro aktuální národní prostředí pro vlákno nebo zadanému národnímu prostředí.

## <a name="remarks"></a>Poznámky

Toto je vnitřní funkce, která CRT používá k načtení aktuální hodnota [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) – makro z úložiště thread local. Doporučujeme použít `MB_CUR_MAX` – makro ve vašem kódu pro přenositelnost.

`__mb_cur_max` – Makro je pohodlný způsob, jak volat `___mb_cur_max_func()` funkce. `__p___mb_cur_max` Funkce je definována pro kompatibilitu s Visual C++ 5.0 a starších verzí.

Vnitřní funkce CRT jsou specifický pro implementaci a může změnit jednotlivých vydání. Nedoporučujeme jejich použití ve vašem kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Viz také:

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
