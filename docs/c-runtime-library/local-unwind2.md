---
title: _local_unwind2 – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
dev_langs:
- C++
helpviewer_keywords:
- _local_unwind2 function
- local_unwind2 function
ms.assetid: 44f1fa82-e01e-490f-a6e6-18fc6811c28c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47227d4be0ad1c5145a9064d11b4ea633c7d7fc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035783"
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