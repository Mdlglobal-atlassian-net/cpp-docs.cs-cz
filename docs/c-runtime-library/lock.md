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
ms.openlocfilehash: 666fdb8febebe133ae09ef3632cb38b6527d1210
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944489"
---
# <a name="_lock"></a>_lock

Získá zámek s více vlákny.

> [!IMPORTANT]
>  Tato funkce je zastaralá. Počínaje verzí Visual Studio 2015 není k dispozici v CRT.

## <a name="syntax"></a>Syntaxe

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parametry

*locknum*<br/>
pro Identifikátor zámku, který se má získat.

## <a name="remarks"></a>Poznámky

Pokud zámek již byl získán, tato metoda přesto získá zámek a způsobí interní chybu jazyka C run-time (CRT). Pokud metoda nemůže získat zámek, ukončí se s závažnou chybou a kód chyby nastaví na `_RT_LOCK`.

## <a name="requirements"></a>Požadavky

**Zdroj:** mlock. c

## <a name="see-also"></a>Viz také:

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
