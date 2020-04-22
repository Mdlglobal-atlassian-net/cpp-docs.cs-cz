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
ms.openlocfilehash: 9ab7cab2209dc2e02cacca6d540927aa39dc3965
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745385"
---
# <a name="_lock"></a>_lock

Získá zámek s více vlákny.

> [!IMPORTANT]
> Tato funkce je zastaralá. Počínaje Visual Studio 2015, není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```cpp
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
