---
title: _local_unwind2
ms.date: 11/04/2016
apiname:
- _local_unwind2
apilocation:
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- _local_unwind2
- local_unwind2
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
ms.openlocfilehash: 8ae5c3937c9dedc54f0a936b91963419d59f79cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535405"
---
# <a name="localunwind2"></a>_local_unwind2

Vnitřní funkce CRT. Spustí všechny obslužné rutiny ukončení, které jsou uvedené v tabulce uvedené oboru.

## <a name="syntax"></a>Syntaxe

```
void _local_unwind2(
   PEXCEPTION_REGISTRATION xr,
   int stop
);
```

#### <a name="parameters"></a>Parametry

*XR*<br/>
[in] Registrační záznam, který je přidružený jeden rozsah tabulky.

*Stop*<br/>
[in] Lexikální úroveň, která označuje, kde `_local_unwind2` by se měla zastavit.

## <a name="remarks"></a>Poznámky

Tato metoda se používá pouze pomocí prostředí za běhu. Nevolejte metodu v kódu.

Když tato metoda se spouští obslužné rutiny ukončení, začne na aktuální úrovni lexikální a funguje směrem nahoru lexikální úrovní, dokud nebude dosaženo úrovně, který je označen `stop`. Nespouští obslužné rutiny ukončení na úrovni, který je označen `stop`.

## <a name="see-also"></a>Viz také

[Abecední seznam odkazů na funkce](../c-runtime-library/reference/crt-alphabetical-function-reference.md)