---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
api_name:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: a7dd7d74992aeddffead1c6ef0d52cbc69848dad
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957289"
---
# <a name="___setlc_active_func-___unguarded_readlc_active_add_func"></a>___setlc_active_func, ___unguarded_readlc_active_add_func

ZASTARALÉ. CRT exportuje tyto interní funkce pouze pro zachování binární kompatibility.

## <a name="syntax"></a>Syntaxe

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>Návratová hodnota

Vrácená hodnota není významná.

## <a name="remarks"></a>Poznámky

I když interní funkce `___setlc_active_func` CRT a `___unguarded_readlc_active_add_func` jsou zastaralé a již nejsou používány, jsou exportovány knihovnou CRT pro zachování binární kompatibility. Původní účel, `___setlc_active_func` který vrátí počet aktuálně aktivních volání `setlocale` funkce. Původní účelem `___unguarded_readlc_active_add_func` bylo vrátit počet funkcí, které odkazovaly na národní prostředí, aniž byste je museli zamykat.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|žádná|

## <a name="see-also"></a>Viz také:

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
