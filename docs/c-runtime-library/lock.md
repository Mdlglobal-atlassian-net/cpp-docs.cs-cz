---
title: _lock
ms.date: 11/04/2016
api_name:
- _lock
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: 30cd84f008c7174d767ecf5e2b744a58b21e5000
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351087"
---
# <a name="_lock"></a>_lock

Získá zámek s více vlákny.

> [!IMPORTANT]
> Tato funkce je zastaralá. Počínaje Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parametry

*locknum*<br/>
[v] Identifikátor zámku získat.

## <a name="remarks"></a>Poznámky

Pokud zámek již byla získána, tato metoda získá zámek stejně a způsobí vnitřní C run-time (CRT) chyba. Pokud metoda nemůže získat zámek, ukončí se s závažnou chybou a nastaví kód chyby na `_RT_LOCK`.

## <a name="requirements"></a>Požadavky

**Zdroj:** mlock.c

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
