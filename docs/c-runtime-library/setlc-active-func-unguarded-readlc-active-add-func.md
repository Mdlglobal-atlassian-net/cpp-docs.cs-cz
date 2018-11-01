---
title: ___setlc_active_func ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: 23095bb13108ec9fde2b168035009f440e9d96f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525775"
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func ___unguarded_readlc_active_add_func

ZASTARALÉ. CRT exportuje tyto vnitřní funkce pouze pro zachování binární kompatibilitu.

## <a name="syntax"></a>Syntaxe

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota není důležité.

## <a name="remarks"></a>Poznámky

I když vnitřní funkce CRT `___setlc_active_func` a `___unguarded_readlc_active_add_func` jsou zastaralé a už nebude používat, jsou exportovány knihovnou CRT pro zachování binární kompatibilitu. Původní účelem `___setlc_active_func` bylo vrátí počet aktuálně aktivních volání `setlocale` funkce. Původní účelem `___unguarded_readlc_active_add_func` bylo vrátí počet funkcí, které odkazuje národní prostředí bez nutnosti používat jenom ho.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|žádná|

## <a name="see-also"></a>Viz také

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)