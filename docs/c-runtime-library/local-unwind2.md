---
title: _local_unwind2
ms.date: 11/04/2016
api_name:
- _local_unwind2
api_location:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: cbcc0c6177ba4cc449daf6a385a7cce53b8c1230
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745325"
---
# <a name="_local_unwind2"></a>_local_unwind2

Interní funkce CRT. Spustí všechny obslužné rutiny ukončení, které jsou uvedeny v tabulce uvedeného oboru.

## <a name="syntax"></a>Syntaxe

```cpp
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Parametry

*Xr*<br/>
[v] Záznam registrace, který je přidružen k jedné tabulce oboru.

*Stop*<br/>
[v] Lexikální úroveň, `_local_unwind2` která označuje, kde by měl zastavit.

## <a name="remarks"></a>Poznámky

Tato metoda se používá pouze v prostředí za běhu. Nevolejte metodu v kódu.

Když tato metoda provede obslužné rutiny ukončení, spustí se na aktuální lexikální úrovni a `stop`pracuje svou cestu nahoru v lexikálních úrovních, dokud nedosáhne úrovně, která je označena . Neprovádí obslužné rutiny ukončení na `stop`úrovni, která je označena .

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
